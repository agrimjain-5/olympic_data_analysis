# Olympic Games Analysis 🏅

An interactive data analysis project that visualizes historical performance data from the Summer Olympic Games using SQL Server and Power BI.

## 📊 Project Overview

This project demonstrates end-to-end data analysis skills by collecting, transforming, and visualizing Olympic Games data to create insights into countries' historical performances. The interactive dashboard enables users to explore performance trends by selecting specific countries, sports, competitors, and time periods.

## ✨ Features

- **Interactive Dashboard**: Filter by country, sport, competitor, year, and medal type
- **Historical Analysis**: Track performance trends across multiple Olympic Games  
- **Data Transformations**: Clean and structured data using SQL queries
- **Advanced Analytics**: Custom DAX measures for competitor and medal calculations
- **Visual Insights**: Clear charts and graphs showing Olympic performance patterns

## 🛠️ Technologies Used

- **SQL Server**: Database management and data transformation
- **Power BI**: Interactive dashboard creation and data visualization  
- **T-SQL**: Data querying and manipulation
- **DAX**: Advanced calculations and measures

## 📁 Data Source

The dataset is sourced from a comprehensive Olympic Games database backup file:
- **Source**: [Olympic Games Database](https://www.dropbox.com/s/3sxwx52o3x8ozj7/olympic_games.bak?dl=0)
- **Coverage**: Summer Olympic Games historical data
- **Content**: Athlete information, events, medals, and performance statistics

## 🚀 Getting Started

### Prerequisites
- SQL Server Management Studio
- Power BI Desktop
- Access to the Olympic Games database backup file

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/agrimjain-5/olympic_data_analysis.git
   cd olympic_data_analysis
   ```

2. **Restore Database**
   - Download the database backup file from the provided link
   - Restore the `olympic_games.bak` file in SQL Server Management Studio

3. **Run SQL Transformations**
   - Execute the provided SQL script to create the transformed view
   - Verify data has been properly processed

4. **Open Power BI Report**
   - Open Power BI Desktop
   - Connect to the SQL Server database
   - Load the transformed Olympic Games view

## 🔧 Data Transformation

### SQL Query Example
The main transformation query structures and cleans the raw Olympic data:

```sql
SELECT
    [ID],
    [Name] AS 'Competitor Name',
    CASE WHEN SEX = 'M' THEN 'Male' ELSE 'Female' END AS Sex,
    [Age],
    CASE	
        WHEN [Age] < 18 THEN 'Under 18'
        WHEN [Age] BETWEEN 18 AND 25 THEN '18-25'
        WHEN [Age] BETWEEN 25 AND 30 THEN '25-30'
        WHEN [Age] > 30 THEN 'Over 30'
    END AS [Age Grouping],
    [Height],
    [Weight],
    [NOC] AS 'Nation Code',
    LEFT(Games, CHARINDEX(' ', Games) - 1) AS 'Year',
    [Sport],
    [Event],
    CASE WHEN Medal = 'NA' THEN 'Not Registered' ELSE Medal END AS Medal
FROM [olympic_games].[dbo].[athletes_event_results]
WHERE RIGHT(Games,CHARINDEX(' ', REVERSE(Games))-1) = 'Summer'
```

### DAX Calculations
Key measures created for analysis:

```dax
# of Competitors = DISTINCTCOUNT('Olympic Games Data'[ID])

# of Medals = 
CALCULATE (
    COUNTROWS('Olympic Games Data'),
    FILTER (
        'Olympic Games Data',
        'Olympic Games Data'[Medal] = "Bronze"
            || 'Olympic Games Data'[Medal] = "Silver"
            || 'Olympic Games Data'[Medal] = "Gold"
    )
)
```

## 📈 Dashboard Features

- **Country Performance**: Historical medal counts and trends by nation
- **Sport Analysis**: Performance breakdown by individual sports
- **Competitor Insights**: Individual athlete statistics and achievements
- **Time Series Analysis**: Trends across different Olympic Games
- **Interactive Filtering**: Dynamic selection of countries, years, and sports

## 📸 Dashboard Preview

*Dashboard screenshot will be displayed here*

![Olympic Games Dashboard](https://via.placeholder.com/800x400/4472C4/FFFFFF?text=Olympic+Games+Dashboard)

## 📁 Project Structure

```
olympic_data_analysis/
│
├── README.md
├── DataAnalystProject_SQL_PBI_OlympicGamesAnalysis.sql
├── Link-to-Olympic-Games-Data.txt
├── Olympic-Games-Portfolio-Project.docx
└── images/
    └── dashboard_screenshot.png
```

## 🎯 Key Insights

- Historical performance trends across different countries
- Medal distribution patterns by sport and gender
- Age group analysis of Olympic competitors
- Evolution of Olympic Games participation over time

## 🔍 Usage Examples

1. **Analyze Country Performance**: Select a specific country to view their historical Olympic performance
2. **Compare Sports**: Filter by sport to see which countries dominate specific events
3. **Track Trends**: Use the year filter to observe performance evolution over time
4. **Competitor Analysis**: Search for specific athletes to view their Olympic journey

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the project
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

## 📞 Contact

**Agrim Jain**
- Email: agrim0233@gmail.com
- LinkedIn: [linkedin.com/in/agrim-jain-a13258218](https://linkedin.com/in/agrim-jain-a13258218/)
- GitHub: [@agrimjain-5](https://github.com/agrimjain-5)

## 🙏 Acknowledgments

- Olympic Games database providers
- Power BI community for visualization inspiration
- SQL Server documentation and community resources

---

⭐ **If you found this project helpful, please give it a star!** ⭐