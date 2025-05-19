# Ex05 Image Carousel
## Date:19-05-2025

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
```
## DEVELOPED BY : NARRA RAMYA

## REGISTER NUMBER: 212223040128
```
## Image Carousel.js
```
// src/ImageCarousel.js
import React, { useState, useEffect } from 'react';

const ImageCarousel = ({ images }) => {
  const [currentIndex, setCurrentIndex] = useState(0);

  const nextImage = () => {
    setCurrentIndex((currentIndex + 1) % images.length);
  };

  const prevImage = () => {
    setCurrentIndex((currentIndex - 1 + images.length) % images.length);
  };

  useEffect(() => {
    const interval = setInterval(nextImage, 3000);
    return () => clearInterval(interval);
  }, [currentIndex, images.length]);

  return (
    <div style={styles.carousel}>
      <div style={styles.imageContainer}>
        <img
          src={images[currentIndex].url}
          alt={images[currentIndex].title}
          style={styles.image}
        />
      </div>
      <h3>{images[currentIndex].title}</h3>
      <div style={styles.buttons}>
        <button onClick={prevImage}>Previous</button>
        <button onClick={nextImage}>Next</button>
      </div>
    </div>
  );
};

const styles = {
  carousel: {
    width: '90%',
    maxWidth: '700px',
    margin: '40px auto',
    textAlign: 'center',
    backgroundColor: '#f4f4f4',
    padding: '20px',
    borderRadius: '12px',
    boxShadow: '0 0 10px rgba(0,0,0,0.1)',
  },
  imageContainer: {
    display: 'flex',
    justifyContent: 'center',
    alignItems: 'center',
    height: '400px',
    backgroundColor: '#fff',
    marginBottom: '10px',
  },
  image: {
    maxWidth: '100%',
    maxHeight: '100%',
    objectFit: 'contain',
    borderRadius: '8px',
  },
  buttons: {
    marginTop: '10px',
    display: 'flex',
    justifyContent: 'center',
    gap: '10px',
  },
};

export default ImageCarousel;

```
## APP.CSS
```
/* src/App.css */

.App {
  text-align: center;
}

footer.footer {
  background-color: #f8f9fa;
  border-top: 1px solid #e9ecef;
  margin-top: 30px;
  padding: 20px;
  width: 100%;
  text-align: center;
}

.footer-content {
  max-width: 600px;
  margin: 0 auto; /* This centers the content */
  font-size: 16px;
  color: #333;
}

@keyframes App-logo-spin {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}

```
## APP.JS
```
// src/App.js
import React from 'react';
import ImageCarousel from './ImageCarousel';
import './App.css'; // Ensure styles are applied

const App = () => {
  const landmarks = [
    {
      title: 'Eiffel Tower, France',
      url: 'https://upload.wikimedia.org/wikipedia/commons/a/a8/Tour_Eiffel_Wikimedia_Commons.jpg',
    },
    {
      title: 'Statue of Liberty, USA',
      url: 'https://upload.wikimedia.org/wikipedia/commons/a/a1/Statue_of_Liberty_7.jpg',
    },
    {
      title: 'Taj Mahal, India',
      url: 'https://upload.wikimedia.org/wikipedia/commons/d/da/Taj-Mahal.jpg',
    },
  ];

  return (
    <div>
      <h2 style={{ textAlign: 'center', marginTop: '20px' }}>
        🌍 Famous Landmarks Carousel
      </h2>
      <ImageCarousel images={landmarks} />
      <footer className="footer">
        <div className="footer-content">
          <p>Created By: <strong>NARRA RAMYA</strong></p>
          <p>Reg No: <strong>212223040128</strong></p>
        </div>
      </footer>
    </div>
  );
};

export default App;

```
## INDEX.JS
```
// src/index.js
import React from 'react';
import ReactDOM from 'react-dom/client';
import App from './App';

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<App />);

```



## OUTPUT
![image](https://github.com/user-attachments/assets/557995d3-5cd1-4345-89e3-9a99c751b29a)

![image](https://github.com/user-attachments/assets/360442ec-b4b9-4490-a6e0-ea57d4b7a85d)

![image](https://github.com/user-attachments/assets/5a796b78-4419-4c89-87d6-cf16cf0f95ba)

## RESULT
The program for creating Image Carousel using React is executed successfully.
