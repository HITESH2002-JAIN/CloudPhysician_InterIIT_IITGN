
<!-- PROJECT LOGO -->
<br />
<p align="center">
  <h1 align="center"> CloudPhysician Inter IIT</h1>

  <p align="center">
  </p>
</p>



<!-- TABLE OF CONTENTS -->
<details open="open">
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>



   <li><a href="#contact">Contact</a></li>
   <li><a href="#acknowledgements">Acknowledgements</a></li>
  </ol>
</details>



<!-- ABOUT THE PROJECT -->
## About The Project

Patient monitoring is a crucial aspect of healthcare, as it allows healthcare professionals to closely track a patient's vital signs and detect any potential issues before they become serious.This project creates a complete pipeline using computer vision to extract important information from the ICU patient's monitor screen, such as heart rate, blood pressure, and oxygen levels. The pipeline takes input images of the monitors with a background and provides extracted vitals as output, along with a digitized graph of the heart rate.

### Built With
The pipeline is built upon multiple object detection model and image processing techniques like pixel clustering, optical character recognition etc. 
<br>
<h4>The major key components of the pipepline are listed below:-</h4>
<br>
<li>
  <b><u>Monitor Extraction model</u></b>
  <br><br>
  This is a object detection model built using [Yolov7](https://github.com/WongKinYiu/yolov7) computer vision model. This model is trained to detect the monitor screen  from the original input image that contains monitor along with some backgrounud. The model predicts the bounding box of the monitor screen, further this monitor      screen is cropped from original image and send as input for the next model<b>(Feature Extraction Model)</b> of the pipeline.
  

</li>
<br><br>
      <b>Sapi5:</b>  Sapi5 is the inbuilt voice package installed in windows. It provides us with 2 voices. We can use either of them in our BOT.
<br><br>
      <b>Web Scrapping:</b> For implemeting features like weather forecast and news headlines, we used web scraping in which we used Bs4 and request modules to import data from web.
<br><br>
      <b>PyQt5 and QtDesigner:</b> This is used to create a graphical user interface for our BOT. 
<br><br>
      <b>Smart Python  Libraries:</b>  Though we have used several libraries, but some major ones are:-
<br>
      <ul>
        <li> 
          Pywhatkit: For sending Whatsaap messages.
        <li>
          SMTPLIB: For sending email messages.
        <li>
          Pyjokes: For adding Joke feature.
        <li>
          PyAutoGui: For automating features like volume up and volume down
             
      
<!-- CONTACT -->
## Contact

* [Ary Pratap Singh](https://www.linkedin.com/in/ary-pratap-singh-73b329207?lipi=urn%3Ali%3Apage%3Ad_flagship3_profile_view_base_contact_details%3BebLXi%2BlvTOyRhTQqbZAXSA%3D%3D)


* Project Link: [https://github.com/Virtual Assistant](https://github.com/AryPratap/BOT-GP-53.git)



<!-- ACKNOWLEDGEMENTS -->
## Acknowledgements
We are thankfull to <b>Metis (the coding club of IIT Gandhinagar)</b> to provide us with this opportunity to make the virtual assistant project under metis summer project challenge. 
