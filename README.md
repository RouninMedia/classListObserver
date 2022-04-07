# classListObserver
A simple `HTML5 MutationObserver` which observes `classLists`.

In this example, whenever the `classList` on an observed element updates, the `MutationObserver` will check to see if *a specific class* has been added.

If the *specific class* has been added, two things will happen:

 - `myFunction()` will be invoked
 - a second `class` will be added to the `classList` to confirm that the addition of the class has been observed

```

const checkClassList = (mutationsList) => {

  for (let mutation of mutationsList) {

    if ((mutation.type === 'attributes') && (mutation.attributeName === 'class')) {

      if ((mutation.target.classList.contains('myAddedClass')) && (mutation.target.classList.contains('myAddedClassObserved') === false)) {
        
        myFunction();
        mutation.target.classList.add('myAddedClassObserved');
      }
    }
  }
}

const classListObserver = new MutationObserver(checkClassList);
myElements.forEach((myElement) => classListObserver.observe(myElement, {attributes: true}));

```
