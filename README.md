# RequestCollectionComputerVisionAPIs
A collection of requests for the communication with different computer vision APIs ([Plant.id](https://www.plant.id/), [Pl@ntNet](https://plantnet.org/en/), [iNaturalist](https://www.inaturalist.org/pages/computer_vision_demo), [NIA](https://observation.org/apps/obsidentify/)).

## Introduction
This script was developed in the context of the project “CS data supporting IAS policy in Europe” caried out by the JRC. It aims at consolidating the framework for CS IAS data in Europe. Towards this objective the aim is inter alia to explore automatized solutions for validation of IAS records in support of citizen science. This entails the identification, testing and provision of species recognition models to support the validation of IAS in Europe. The outmost goal is to improve the current data validation process of the JRC app through automation.

This script is used to send request to four different computer vision APIs and store the results in a .csv file. The APIs that can be accessed are:
 * [Plant.id](https://www.plant.id/): Plant.id is a project developed by the team of the [FlowerChecker company](http://flowerchecker.com/), whereby the main goal is to facilitate the monitoring of invasive and endangered species for a wide range of usage scenarios from business to private use.
 * [Pl@ntNet](https://plantnet.org/en/): The Pl@ntNet project, implemented by a consortium including CIRAD, INRA, INRIA, IRD and the Agropolis Foundation, is a tool which supports the image-based identification of plants (https://identify.plantnet.org/) for both, amateurs and professional.
 * [iNaturalist](https://www.inaturalist.org/pages/computer_vision_demo): The iNaturalist API is developed by [iNaturalist](https://www.inaturalist.org/), a joint initiative by the California Academy of Science and the National Geographic Society. It is able to identify plant and animal species.
 * [NIA](https://observation.org/apps/obsidentify/): The Nature Identification API, is a joint effort by [Observation International](https://observation-international.org/en/), [Naturalis](https://www.naturalis.nl/en) and Intel Corp. It is able to identify plant and animal species.



## Installation
### 1. Clone the repo
```bash
git clone https://github.com/EibSReM/RequestCollectionComputerVisionAPIs.git
cd ReqRequestCollectionComputerVisionAPIs
```

### 2. Installtion of packages 

You can either install python and all packages directly on your or machine or you can use virtual environments like conda.


a) Plain installation

1. Install Python

2. Install Jupyter notebook (more info at https://jupyter.org/install.html) and needed Packages
```bash
pip install notebook
pip install requests
```

b) Using Conda

```bash
conda env create -f environment.yml
conda activate RequestCollectionComputerVisionAPIs
```

### 3. Start the jupyter notebook
```bash
jupyter notebook apiRequests.ipynb
```


## Usage
* Create folder containing all images to test
* run all code chunks including the last one. The last one will perform the analysis. You will asked to enter different details: 
  * Path to the directory where the test images are in
  * the filename in which the results will be saved, if it not exists it will be created
  * The API, which should be used (one of "plantNet","iNaturalist", "plantID", "NIA")
  * User credentials (see [User credentials](#user-credentials))
    * For NIA:
      * E-Mail
      * Password 
    * For the other APIs:
      * Access token
* The result file will have following result:
  * fileName of image, first prediction, score of first prediction, second prediction, score of second prediction, ... 


## User Credentials
For all APIs you need to provide user credentials. How you can get these is described below:

* Plant.id
  * Fill out following form to request an API-key: https://web.plant.id/api-access-request/
* Pl@ntNet
  * Create a Pl@ntNet Developer Account: https://my.plantnet.org/signup
* iNaturalist
  * Create an Account on rapidAPI: https://rapidapi.com/auth/sign-up
  * Write an E-Mail to iNaturalist and ask for access to the VisionAPI on rapidAPI: help@inaturalist.org
* NIA
  * Create an Account on Obervation.org: https://observation.org/accounts/signup/
  * Write an E-Mail to observation.org and ask them to enable your account to access the computer vision model: info@observation.org 
### Number of Requests
The amount of requests needed depends on the number of images to be tested. For each image one request is needed. In our research we tested the APIs with 6 images of by the API covered Invasive Alien Species of union concern. Which results in different test sizes.
* INaturalist API: 432
* NIA: 294
* Pl@ntNet API: 180
* PlantID: 186
### Execution Time
The execution time strongly depends on the internet connection and the response time of the APIs, which often vary. As an example:
To query 150 images with Pl@ntNet took 8:13 minutes, with the CPU time being 1:43 minutes.


