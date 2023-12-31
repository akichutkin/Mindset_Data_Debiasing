[imported from gitlab.infk.ethz.ch]
## MindSet: A human-centric approach to debias your data

## Short description

### Abstract
The rise of deep learning models in automated decision making has raised great concerns about bias and fairness. A main cause of biased models lies in asymmetries in the training datasets, for instance, due to reporting or selection biases. Discovering such artifacts, however, is especially difficult as for many data types there are no common quantitative measures of bias. Therefore, a common approach is to rely on human feedback. This is based on the assumption that a sufficiently large number of human judgements will correctly detect such anomalies. In a former paper, Hu et al.\cite{bias_crowdsource} introduce a three stage study framework to use human feedback to detect biases in visual datasets and ran a small-sample study with encouraging results. Unfortunately, there is no public, dataset-agnostic implementation available that would enable researchers to use this method to clean their self-collected, or even synthetically generated image datasets. To this end, we develop a highly flexible study interface that follows the framework proposed by Hu et al. and present a demo study to highlight the most import features.

### Report
You can find the project report in ```final_report.pdf```

## Team Members
1. Ziyao Shang
2. Andras Strausz
3. Alexander Kichutkin
4. Senthuran Kalananthan

- - -
## Demo version

Currently there is a demo study available with ChatGPT generated responses. To support the evaluation of the interface we implemented the following:
- API call: ```/resetDatabase``` . This can be used to move the demo surveys stage to Stage 1
- Dummy answers for Stage 2 and 3: these answers were also generated by ChatGPT and correspond to 4 clusers, as this was the elbow point.
- pre-registered users: You can login with study administrator rights with ```username: admin```, ```password: admin``` and as a prticipant with ```username:user```, ```password: user```
- To test registration, you can register a new user (even admin by check the correspong box). Users are directly verified, see bug below.
- - - -
## Known Issues

- The email verification process does not work on the deployed version, but works on the local version. As we have no access to the server and this is likely to be caused by some server configuration we could not debug this issue.
- After a longer passive period the user handling process main run into an error. Please go back to homepage and log in again. 
- - -
## Folder Structure
Specify here the structure of you code and comment what the most important files contain

``` bash
├── backend-project
│   ├── Dockerfile
│   ├── MANIFEST.in
│   ├── pyproject.toml
│   ├── README.md
│   ├── setup.py
│   └── src
│       ├── database_check.py
│       ├── preprocessing.py
│       ├── server
│       │   ├── __init__.py
│       │   ├── resources
│       │   │   ├── email_template.html #mail for verification
│       │   │   ├── __init__.py
│       │   └── router
│       │       ├── app.py # FLASK backend
│       │       ├── __init__.py
│       │       └── text_processing_utils.py #utils for processing user inputs
│       └── test_backend.py # tester for development
├── helm
│   ├── charts
│   ├── Chart.yaml
│   ├── files
│   ├── templates
│   │   ├── deployment.yaml
│   │   ├── ingress.yaml
│   │   └── service.yaml
│   └── values.yaml
├── package.json
├── package-lock.json
├── react-frontend
│   ├── package.json
│   ├── package-lock.json
│   ├── public
│   │   ├── favicon.ico
│   │   ├── index.html
│   │   ├── logo192.png
│   │   ├── logo512.png
│   │   ├── manifest.json
│   │   └── robots.txt
│   ├── README.md
│   ├── src
│   │   ├── App.css
│   │   ├── App.test.tsx
│   │   ├── App.tsx
│   │   ├── components
│   │   │   ├── Buttons.css
│   │   │   ├── Cards.css
│   │   │   ├── cluster_vis.tsx
│   │   │   ├── ConfirmRegistration.tsx
│   │   │   ├── Home.css
│   │   │   ├── Home.tsx
│   │   │   ├── images #all images shown on the website
│   │   │   ├── Intro.tsx #Introduction page before starting stage 1
│   │   │   ├── Login.tsx # Login page
│   │   │   ├── NavbarComp.tsx # Upper bar
│   │   │   ├── Overview.tsx # Admin overview page
│   │   │   ├── process_login.tsx # utils for user handling
│   │   │   ├── Register.tsx # registration form
│   │   │   ├── ScatterPlot.css
│   │   │   ├── ScatterPlot.tsx
│   │   │   ├── Summary.css
│   │   │   ├── Summary.tsx # summary overview page
│   │   │   ├── Survey_1_End.tsx 
│   │   │   ├── Survey_1.tsx # Stage 1
│   │   │   ├── Survey_2_End.tsx
│   │   │   ├── Survey_2_Start.tsx
│   │   │   ├── Survey_2.tsx # Stage 2
│   │   │   ├── Survey_3_End.tsx
│   │   │   ├── Survey_3_Start.tsx
│   │   │   ├── Survey_3.tsx # Stage 3
│   │   │   ├── survey_components.tsx # helper function to show images
│   │   │   ├── trippleStateSwitch.tsx #costum button for Stage 3
│   │   │   ├── Userhome_alt1.tsx
│   │   │   ├── UserHome_alt2.tsx
│   │   │   ├── UserHome_og.tsx
│   │   │   ├── UserHome.tsx # Participants overview
│   │   │   └── utils.ts
│   │   ├── index.css
│   │   ├── index.tsx
│   │   ├── logo.svg
│   │   ├── react-app-env.d.ts
│   │   ├── reportWebVitals.ts
│   │   ├── setupTests.ts
│   │   └── types
│   │       ├── data.ts
│   │       └── margin.ts
│   └── tsconfig.json
├── README.md
└── structure.md
```

## Requirements
- python3.8 or better
- npm

Other requirements are contained in the *setup.py* and *package.json* files. **Note:** you may have to comment out the pytorch wheel in *setup.py* depending on your local machine. This was necessary to deploy the website.

## How to Run

To host the website locally:
- clone the repository;
- open a new terminal instance;
- move to the folder where the project has been downloaded using the command ```cd```;
- open the folder called "a10-bias-assessment-with-human-feedback";
To run the backend
- open the backend folder called "backend-project";
- install the requirements with ```pip3 install .```
- start the backend with the command ```python3.8 -m server.router.app```;
To run the frontend
- open a new terminal instance and once again go to the folder called "a10-bias-assessment-with-human-feedback"
- open the frontend folder called "react-frontend";
- start the front end by using the following two commands ```npm install```, ```npm start```;
If all the steps have been successfully executed a new browser window will open automatically.

## Contribution statement

We declare that all memebers of the team contributed equally. Below you find an overview of the topics the individuals worked on:
