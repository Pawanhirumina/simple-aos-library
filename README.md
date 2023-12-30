
# Simple AOS Library
A lightweight JavaScript library for adding scroll-triggered animations to your web projects. Easily integrate animated elements that come into view during scrolling.

## Getting Started
Follow these steps to use the Simple AOS Library in your projects:

### Step 1: Clone the Repository

- Clone this repository to your local machine:
```bash
git clone https://github.com/Pawanhirumina/simple-aos-library.git
```

### Step 2: Include Simple AOS Library Files
- Copy the `aos.js` and `aos.css` files from the cloned repository to your project directory.

### Step 3: Link Simple AOS Library Files in Your HTML
- Include the Simple AOS Library files in the <head> section of your HTML file:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="aos.css">
    <script src="aos.js"></script>
    <title>Your Project with Simple AOS</title>
</head>
<body>

<!-- Your content here -->

<script>
    document.addEventListener('DOMContentLoaded', function () {
        const aosItems = document.querySelectorAll('.aos-item');

        function isElementInViewport(el) {
            const rect = el.getBoundingClientRect();
            return (
                rect.top >= 0 &&
                rect.bottom <= (window.innerHeight || document.documentElement.clientHeight)
            );
        }

        function handleScroll() {
            aosItems.forEach(item => {
                const aosType = item.getAttribute('data-aos');
                const hasAnimationClass = item.classList.contains(`aos-${aosType}`);

                if (isElementInViewport(item) && !hasAnimationClass) {
                    // Add the animation class
                    item.classList.add(`aos-${aosType}`);
                } else if (!isElementInViewport(item) && hasAnimationClass) {
                    // Remove the animation class if the element is no longer in view
                    item.classList.remove(`aos-${aosType}`);
                }
            });
        }

        window.addEventListener('scroll', handleScroll);
        window.addEventListener('resize', handleScroll);

        // Initial check on page load
        handleScroll();
    });
</script>

</body>
</html>
```

### Step 4: Add Simple AOS Classes to Elements
Now, you can add the data-aos attribute to the HTML elements you want to animate:

```html
<div class="aos-item" data-aos="fade-up">
    <h1>Welcome to Your Project</h1>
</div>

<div class="aos-item" data-aos="fade-left">
    <p>This is a simple example of using Simple AOS.</p>
</div>

<div class="aos-item" data-aos="fade-right">
    <p>Scroll down to see animations in action.</p>
</div>
```

### Step 5: Customize and Run Your Project
Customize your animations by adjusting settings in the aos.init() function in the included JavaScript script. Open your HTML file in a web browser, and scroll down to see the animations in action.

That's it! You have successfully integrated the Simple AOS Library into your project. Happy scrolling and animating! 🚀