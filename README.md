# useoutside 

it is custom hooks project 

# useOutsideClick
useOutsideClick: Takes two arguments, ref (a reference to a DOM element) and handler (a function to be called when a click outside the element is detected).

export default function useOutsideClick(ref, handler) {}

# Using useEffect:

The useEffect hook sets up event listeners when the component mounts 
 and cleans them up when the component unmounts.

#Listener Function:

listener(event): This function checks if the click event occurred outside the element referenced by ref.

!ref.current: If the ref is not set, return early.

ref.current.contains(event.target): If the click event’s target is inside the referenced element, return early.

If neither condition is true, the handler function is called with the event.

function listener(event) {
  if (!ref.current || ref.current.contains(event.target)) {
    return;
  }
  handler(event);
}

# Adding Event Listeners:

Adds event listeners for mousedown and touchstart events to the document.

document.addEventListener('mousedown', listener);
document.addEventListener('touchstart', listener);

# Cleaning Up Event Listeners:

The useEffect hook returns a cleanup function that removes the event listeners
 when the component unmounts or when ref or handler changes.

return () => {
  document.removeEventListener('mousedown', listener);
  document.removeEventListener('touchstart', listener);
};


# Conditional Rendering:

{showContent ? (...) : (...)}: Wrap the condition inside braces to evaluate showContent correctly.

If showContent is true, the content inside the <div ref={ref}> will be rendered.

If showContent is false, the button will be rendered.

# State Management:

showContent: Manages whether the content is shown or not.

ref: Holds the reference to the content that should be closed when clicking outside.

# Custom Hook (useOutsideClick):
useOutsideClick(ref,()=>setShowContent(false))

Attaches event listeners to detect clicks outside the referenced element.

Calls the setShowContent(false) handler to close the content if a click outside is detected.


# bisrat Nov 24 2024