## NuCare: iOS Informational Application for Nuclear Medicine Protocols

**Project description:** I completed this project as an intern with the U.S. Nuclear Regulatory Commission, during the summer of 2018. I, along with two other interns, worked to develop a self-guided project within the Office of Nuclear Material Safety and Safeguards. After researching the nuclear medicine field and the role the NRC plays in regulating it, I proposed that we develop a mobile application. The purpose of such an application would be to provide an accessible and integrated information source regarding nuclear medicine and specifically the safety regulations imposed by the NRC to both patients and their families.

### 1. Provide Unified Information Source Regarding Nuclear Medicine Treatments and Diagnostic Tests

My role in the development of this app was mainly on the several existing types of treatments as well as diagnostic tests utilizing radioactive materials. The respective pages for each application covers a variety of important information, from expected radiation levels based on averages to what patients can expect from the process.
<img src="images/EBRTPage.png?raw=true"/>

### 2. UI Interaction
Simple UI interactions via buttons and swipes allow the user to navigate through treatment pages and see more information about particular parts of the process. The application is also properly constrained so as to format correctly on varying device sizes, from iPads to various iPhones.
<img src="images/TreatmentsPage.png?raw=true"/>


### 3. Basic "Radiation Calculator"
Program has a radiation calculator which is regulated by a dictionary, allowing users to select the type of treatment/test they are expecting to get and then returning an approximate radiation amount based on collected data. The application also characterizes this information in an easier, more digestible fashion by developing simple comparisons for the radiation result such as "Radiation Amount = Taking XX Plane Trips".
```Swift
 let natualBackgroundDose = BACKGROUND_DOSE
        let dosage = usedDose/natualBackgroundDose
        var str = ""
        let frac = rationalApproximation(of: dosage)
        if(dosage < 1){
            if(frac.den < 10){
                str = fractionToString(fraction: frac)
            }else{
                str = String((dosage * 100).rounded() / 10)
            }
}
```

For more details see [App Demonstration Video](https://vimeo.com/295086496).
