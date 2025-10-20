# GeoNet Spider

This project is a Web Application and Notebook submission for the **Takiwaehere Geospatial Hackathon** (17–18 April, 2021), where our team won **2nd place at the University of Canterbury**.

**Hackathon Information:**  
[Takiwaehere - The Geospatial Hackathon](https://www.mbie.govt.nz/science-and-technology/science-and-innovation/international-opportunities/new-zealand-r-d/innovative-partnerships/takiwaehere-the-geospatial-hackathon)

---

## Presentation

For more details on the project, you can view our presentation slides:  
[**Download Presentation (PDF)**](./presentation.pdf)

---

## Project Summary

Taking advantage of remote sensing and deep learning, this project used MAXAR-provided data to produce a multiple-image timeline of Christchurch City from 2011 (pre-earthquake) to 2013.  
Using PyTorch, a Python deep learning library, a U-Net convolutional neural network was trained to detect buildings, both residential and industrial.  

The training data was produced manually in ENVI software to train the model. The results from this model were exported as `.png` files and displayed in the final web app.  
Also, the results from the ENVI classification were demonstrated on the web following a time series. The results showed a fall in building numbers in 2012 and then a rise in 2013.

---

## Methodology and Solution

### Motivation

Being based in Christchurch ourselves, it seemed appropriate to complete a project regarding the earthquake of 2011.  
Our past University projects also aligned with this idea, having worked with the disaster in both GIS and non-GIS related assignments.  
An example of this would be the processing and display of vegetation indices for the Christchurch area and how different seasons altered these metrics.

---

### Training Data Generation

Our method for producing a training dataset for deep learning was achieved by supervised classification in ENVI.  
Initially, we created a list of 7 classifications: Green space, residential area, car parks, roads, industrial area, under-developing area, and water.  

After very time-consuming manual human interpretation, we found that the street and car park were mixed in the classification results, for the reason that they were too similar in color and patterns.  
Therefore, we finally decided to only focus on the detection of buildings including residential and industrial types.

The final solution we used for the training dataset involved ENVI and ArcGIS.  
The pan-sharpened images were used to make the training dataset because of their highly defined edges.  
We successfully extracted buildings from the satellite images by applying a band threshold on the blue band, because of its shorter wavelength.  

We inspected the area of each building and filtered out the lower values as it is usually shown as noise.  
Finally, we uploaded the results to ArcGIS Online.

---

### Machine Learning and Deep Learning

The whole machine learning section is in one Jupyter Notebook.  
We used the image of Central Christchurch in February 2011 and the labels for buildings obtained by ENVI to train a machine learning model.  
We cut the image into small pieces and split them into training (70%), validation (10%), and test (20%) datasets.

PyTorch was the deep learning framework we used.  
The model applied the U-Net architecture.  
We used transfer learning and tuned the pretrained model with the data and the labels.  

Then the model performed semantic segmentation and automatically labeled the images in June 2012, October 2012, and March 2013 respectively.  
Finally, we displayed the changes in buildings in the whole city center and in a small area with time.

---

### Web App and Output

The web app has an Angular webframe foundation using libraries such as Chart.js and esri-loader to produce a visually pleasing interactive map.  
Other general features have been added to make it feel like a real website instead of a singular map.  

The map is able to show the different times of our chosen period and where buildings have been detected by our classification system.  
A graph is also displayed showing the area of total buildings over years in the study area.  

The final web app utilizes the final raster outputs overlay from the deep learning, which can be found in the layer list at the top-left corner.

![Application Output Example](./assets/img/results.png)

---

### Conclusion

The solutions given by this Hackathon project work efficiently online, which is friendly to public users, even users who lack spatial knowledge.  

The solution is not perfect, for the following two reasons:  
1. Due to limited computer capacity, we were not able to get output images from deep learning models because we didn't have enough storage to load the processing.  
2. The limited time to make a decent classification in ENVI was very time-consuming.  

If we had enough time, we could make a more accurate training dataset, which is crucial to the performance of our deep learning model.  
Thus, under the limited conditions both in time and facilities, this solution can largely align to our original target, which is detecting the changes of landscapes over time.

---

## Competitive Advantage

### Alternative Approaches and Uniqueness

Changes in cities can be extracted manually from sources like fieldwork and historical maps, which is time-consuming.  
Geospatial software, such as ENVI and ArcGIS, can also recognize the changes using satellite images; however, it always lacks accuracy.  

The method proposed by our team can provide an enhanced classification metric using the power of artificial intelligence.  
Although we only created a basic model for building detection, this idea could be greatly enhanced to include many different objects visible through satellite imagery.

---

### Target Audience

Within the 24hr scope, our target group of users is anyone who wants to understand the changes happening in Christchurch in terms of building rates.  

In a wider context with an enhanced model, our users could be governments, citizens, city planners, businesses, etc.  
This could potentially be developed into an automated intelligence gathering system that can detect unusual changes in urban landscapes all over the world.

---

### Future Prospects

Improvement of the deep learning model would greatly enhance our results.  
This could come in the form of a higher resolution output or additional training data to increase the accuracy of the classification system.

---

## Our Hackathon Experience

As a team of four, we completed this project within the demanding 24-hour timeframe of the hackathon.  
The experience was a testament to effective collaboration and efficient task delegation.  

Each member took ownership of a specific part of the project, from data processing and model training to front-end web development.  
This division of labor allowed us to work in parallel and make rapid progress.  

Constant communication and integration of our individual parts were key to building a cohesive and functional final product under pressure.  
It was an intense but incredibly rewarding experience that highlighted our team's synergy and problem-solving capabilities.

---

## Tools and Technology

### Image Processing
* ENVI 5.6  
* ArcGIS Pro 2.6.3  

### Deep Learning Modelling
* Google Colab Pro (GPU)  
* PyTorch  
* NumPy  
* Pillow  
* Matplotlib  
* OpenCV  
* scikit-learn  
* U-Net  

### Web Development
* ArcGIS API for JavaScript 4.18  
* Angular  
* WebStorm 2021.1  

---

## Viewing the Application

This project consists of a set of static web files.  
To view the application, you can serve the files using a simple local web server.

1. Make sure you have Node.js installed.  
2. Install a simple web server package like `http-server` globally:  
   ```bash
   npm install -g http-server
   ```
3. Navigate to the project's root directory (`/c/Portfolio/Website`) in your terminal.  
4. Start the server:  
   ```bash
   npx http-server
   ```
5. Open your web browser and navigate to the address provided by `http-server` (usually `http://127.0.0.1:8080`).  
T e s t :   i g n o r e   d e p l o y   o n   R E A D M E   u p d a t e  
 