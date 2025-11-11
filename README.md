# Ex05 Image Carousel
## Date:11-11-2025
## NAME: Vinuthaa NN
## REG NO: 212224040362

## AIM
To create a Image Carousel using React 

## ALGORITHM
### STEP 1 Initial Setup:
Input: A list of images to display in the carousel.

Output: A component displaying the images with navigation controls (e.g., next/previous buttons).

### Step 2 State Management:
Use a state variable (currentIndex) to track the index of the current image displayed.

The carousel starts with the first image, so initialize currentIndex to 0.

### Step 3 Navigation Controls:
Next Image: When the "Next" button is clicked, increment currentIndex.

If currentIndex is at the end of the image list (last image), loop back to the first image using modulo:
currentIndex = (currentIndex + 1) % images.length;

Previous Image: When the "Previous" button is clicked, decrement currentIndex.

If currentIndex is at the beginning (first image), loop back to the last image:
currentIndex = (currentIndex - 1 + images.length) % images.length;

### Step 4 Displaying the Image:
The currentIndex determines which image is displayed.

Using the currentIndex, display the corresponding image from the images list.

### Step 5 Auto-Rotation:
Set an interval to automatically change the image after a set amount of time (e.g., 3 seconds).

Use setInterval to call the nextImage() function at regular intervals.

Clean up the interval when the component unmounts using clearInterval to prevent memory leaks.

## PROGRAM
app.jsx
```
import React from 'react';
import ImageCarousel from './imageCarousel';

function App() {
  const images = [
    "https://images.unsplash.com/photo-1529626455594-4ff0802cfb7e",
    "https://images.unsplash.com/photo-1519125323398-675f0ddb6308",
    "https://images.unsplash.com/photo-1507525428034-b723cf961d3e"
  ];

  return (
    <div className="App">
      <ImageCarousel images={images} />
    </div>
  );
}

export default App;
```
img-carousel.jsx
```
import React, { useState, useEffect, useCallback } from 'react';

const images = [
  'https://picsum.photos/id/237/600/400',
  'https://picsum.photos/id/238/600/400',
  'https://picsum.photos/id/239/600/400'
];


function ImageCarousel() {
  const [currentIndex, setCurrentIndex] = useState(0);

  const nextImage = useCallback(() => {
    setCurrentIndex((prevIndex) => (prevIndex + 1) % images.length);
  }, []);

  const prevImage = () => {
    setCurrentIndex((prevIndex) =>
      (prevIndex - 1 + images.length) % images.length
    );
  };

  useEffect(() => {
    const interval = setInterval(() => {
      nextImage();
    }, 3000);

    return () => clearInterval(interval);
  }, [nextImage]);

  return (
    <div style={{ textAlign: 'center' }}>
      <h1>React Image Carousel</h1>
      <img
        src={images[currentIndex]}
        alt="carousel"
        style={{ width: '400px', borderRadius: '10px' }}
      />
      <br />
      <button onClick={prevImage}>Previous</button>
      <button onClick={nextImage} style={{ marginLeft: '10px' }}>
        Next
      </button>
    </div>
  );
}

export default ImageCarousel;
```
index.css
```
/* Reset and Font */
body {
  margin: 0;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  background: linear-gradient(135deg, #f8f9fa, #d6e4f0);
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

/* Carousel Container */
.carousel-container {
  background-color: #ffffffdd;
  padding: 40px;
  border-radius: 16px;
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.1);
  text-align: center;
}

/* Title */
.carousel-container h1 {
  font-size: 2.5rem;
  margin-bottom: 30px;
  color: #2c3e50;
}

/* Image Styling */
.carousel-container img {
  width: 100%;
  max-width: 500px;
  height: auto;
  border-radius: 16px;
  box-shadow: 0 6px 20px rgba(0, 0, 0, 0.25);
  transition: transform 0.3s ease;
}

.carousel-container img:hover {
  transform: scale(1.03);
}

/* Button Container */
.button-container {
  margin-top: 20px;
}

/* Navigation Buttons */
.button-container button {
  background-color: #2c3e50;
  color: white;
  border: none;
  padding: 12px 24px;
  margin: 0 10px;
  border-radius: 8px;
  cursor: pointer;
  font-size: 1rem;
  transition: background-color 0.3s ease;
}

.button-container button:hover {
  background-color: #34495e;
}
```


## OUTPUT
<img width="758" height="433" alt="image" src="https://github.com/user-attachments/assets/0846a245-e69b-4ccd-8c0e-c504efed1cd4" />

<img width="770" height="418" alt="image" src="https://github.com/user-attachments/assets/d9ece9ac-efa0-4d19-9b22-e3627e235cf6" />



## RESULT
The program for creating Image Carousel using React is executed successfully.
