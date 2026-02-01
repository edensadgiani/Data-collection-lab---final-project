![header](https://capsule-render.vercel.app/api?type=waving&height=300&color=A5BECC&fontColor=365486&text=Context-Aware%20Rental%20Probability%20Model-nl-for%20Dynamic%20Pricing&desc=Final%20Project&fontAlign=50&descSize=30&descAlign=50&fontAlignY=31&fontSize=43&descAlignY=63)

![header](https://capsule-render.vercel.app/api?type=transparent&color=A5BECC&height=65&reversal=true&fontSize=24&fontColor=365486&text=The%20Faculty%20of%20Data%20and%20Decisions%20Science%20-nl-%20&desc=%20Technion%20-%20Israel%20Institute%20of%20Technology&descSize=18&descAlignY=73&fontAlign=50&animation=fadeIn&textBg=false&section=header&stroke=243A73&strokeWidth=0&theme=holi)

![footer](https://capsule-render.vercel.app/api?type=waving&color=A5BECC&height=100&section=footer&text=%20-nl-%20Winter%202025/26%20%20&fontSize=16&fontAlign=50&fontColor=365486&theme=holi)

![header](https://capsule-render.vercel.app/api?type=soft&color=293B5F&height=45&section=header2&text=Authors&fontSize=28&fontAlign=7&fontColor=EEF5FF&reversal=false&theme=holi)
> Noa Bamberger noabamberger@campus.technion.ac.il
>
> Amit Kedem-Weizman kedem.amit@campus.technion.ac.il
> 
> Eden Sadgiani eden.sa@technion.ac.il
> 

![header](https://capsule-render.vercel.app/api?type=soft&color=293B5F&height=45&section=header&text=Project%20Overview&fontSize=28&fontAlign=14&fontColor=EEF5FF&reversal=true&theme=holi)

This project develops a Smart Pricing System for Airbnb hosts. By integrating internal listing data with external

signals like weather and holidays, it moves beyond host intuition. Using XGBoost and Logistic Regression, it 

optimizes revenue through demand-ranked dynamic adjustments.


![header](https://capsule-render.vercel.app/api?type=soft&color=293B5F&height=45&section=header&text=Datasets&fontSize=28&fontAlign=7&fontColor=EEF5FF&reversal=true&theme=holi)

The system integrates multiple data sources:

- **Airbnb Listings Data**
  Property characteristics, pricing details, availability, reviews, and location metadata.

- **Weather Data**
Historical and forecast data retrieved via the Open-Meteo API.

- **Public Holidays**
National holiday calendars collected using the Nager.Date API.

- **Points of Interest (POI)**
Geographic features (landmarks, transport hubs, attractions) extracted from OpenStreetMap (Nominatim & Overpass APIs) and aggregated within multiple distance radii.


All datasets were processed using PySpark and stored in Parquet format.

![header](https://capsule-render.vercel.app/api?type=soft&color=293B5F&height=45&section=header&text=Methodology&fontSize=28&fontAlign=11&fontColor=EEF5FF&reversal=true&theme=holi)

The pricing framework follows a **predict-then-adjust** approach:

- **XGBoost Regression**
Used to estimate a baseline nightly price for a property based on static attributes and location-level features.

- **Logistic Regression**
Used to estimate the probability of rental for a specific property on a given day, incorporating contextual variables such as weather, holidays, and price.

Instead of full price optimization, days are **ranked by predicted rental probability**, and prices are dynamically adjusted (±10%) for high- and low-demand periods.


![header](https://capsule-render.vercel.app/api?type=soft&color=293B5F&height=45&section=header&text=Key%20Results&fontSize=28&fontAlign=11&fontColor=EEF5FF&reversal=true&theme=holi)

- The XGBoost model significantly outperforms city-level baseline pricing, explaining a substantial portion of price variance.

- The logistic regression model provides well-calibrated probability estimates, suitable for demand estimation rather than binary classification.

- Demand-ranked pricing produces *clear and interpretable dynamic price variations* aligned with contextual demand signals.


![header](https://capsule-render.vercel.app/api?type=soft&color=293B5F&height=45&section=header&text=Limitations&fontSize=28&fontAlign=11&fontColor=EEF5FF&reversal=true&theme=holi)

- Rental demand is inferred from availability rather than transaction logs.

- The analysis focuses on top data-rich cities and a restricted time window.

- Real-time deployment was simulated due to API rate and resource constraints.



![header](https://capsule-render.vercel.app/api?type=soft&color=293B5F&height=45&section=header&text=Conclusion&fontSize=28&fontAlign=11&fontColor=EEF5FF&reversal=true&theme=holi)

This project demonstrates that incorporating external contextual signals, particularly weather and holidays, 

adds meaningful value to short-term rental pricing models.

The shift from full optimization to probability-based demand ranking highlights the importance of balancing model 

complexity with interpretability and practical deployment considerations.

![header](https://capsule-render.vercel.app/api?type=soft&color=293B5F&height=45&section=header&text=Acknowledgment&fontSize=28&fontAlign=14&fontColor=EEF5FF&reversal=true&theme=holi)

Developed for the Data Collection Lab - 00940290 by Noam Cohen, Technion. <br>
All Rights Reserved.
