# 🚛 Mining Operations Efficiency Analytics Platform

A comprehensive data analytics solution for mining operations that provides real-time operational efficiency insights, productivity analysis, and performance optimization through advanced time usage modeling and interactive dashboards.

## 🎯 Project Overview

This platform transforms raw mining operations data into actionable insights through a modern data architecture built on Databricks, featuring:

- **Real-time Data Processing** with Lakeflow Declarative Pipelines
- **Advanced Time Usage Analysis** with efficiency mapping and productivity loss identification
- **Interactive Dashboards** with professional visualizations and drill-down capabilities
- **Medallion Architecture** (Bronze → Silver → Gold) for data quality and governance
- **Synthetic Data Generation** for testing and demonstration purposes

## 🏗️ Architecture

### **Data Flow**
```
Synthetic Data Generator → Unity Catalog Volume → Lakeflow Pipeline → Gold Tables → Dashboard
```

### **Medallion Architecture**
- **Bronze Layer**: Raw data ingestion (4 streaming tables)
- **Silver Layer**: Data quality and transformations (4 materialized views)
- **Gold Layer**: Business analytics and insights (5 materialized views)

## 📁 Project Structure

```
camp_optimization/
├── setup/                                    # Data generation and setup
│   ├── 01_setup_unity_catalog.ipynb         # Unity Catalog configuration
│   └── 02_generate_simplified_data_80_percent.ipynb  # Synthetic data generator
├── pipelines/                               # Data processing pipelines
│   └── 04_simplified_pipeline_clean.ipynb  # Lakeflow declarative pipeline
├── dashboards/                              # Visualization dashboards
│   └── mining_operations_demo_dashboard.lvdash.json  # Demo dashboard
├── requirements.txt                         # Python dependencies
└── README.md                               # This file
```

## 🚀 Quick Start

### **Prerequisites**
- Databricks workspace with Unity Catalog enabled
- Python 3.8+ environment
- Access to create catalogs, schemas, and volumes

### **1. Setup Unity Catalog**
```bash
# Run the setup notebook
databricks workspace import 01_setup_unity_catalog.ipynb
```

### **2. Generate Synthetic Data**
```bash
# Run the data generator
databricks workspace import 02_generate_simplified_data_80_percent.ipynb
```

### **3. Deploy Data Pipeline**
```bash
# Run the Lakeflow pipeline
databricks workspace import 04_simplified_pipeline_clean.ipynb
```

### **4. Import Dashboard**
```bash
# Import the demo dashboard
databricks workspace import mining_operations_demo_dashboard.lvdash.json
```

## 📊 Data Model

### **Core Entities**

#### **Trucks**
- 50 mining trucks with different types and capacities
- Performance tracking and efficiency analysis

#### **Truck Productivity Events**
- 30-60 events per truck per day (67,500+ total events)
- **85% Productive** events (Loading, Traveling, Dumping, Available, En Route)
- **3% Breakdown** events (Engine Failure, Hydraulic Issue, Tire Puncture, etc.)
- **12% Delay** events (Weather Delay, Traffic Delay, Loading Delay, etc.)

#### **Truck Cycles**
- Loading and dumping transactions with timing data
- Performance metrics and cycle duration analysis

#### **Time Usage Model**
- Event categorization for operational efficiency analysis
- Target efficiency percentages and productivity flags
- Subcategory classification (Operations, Mechanical, External, etc.)

### **Data Volume**
- **50 trucks** across **30 days** of operations
- **~67,500 total events** with realistic operational patterns
- **Variable daily activity** with weekend effects
- **Time-based analysis** (Morning, Afternoon, Evening, Night)

## 🔧 Technical Components

### **Data Generation (`setup/`)**

#### **Unity Catalog Setup**
- Creates `mining_operations` catalog
- Sets up `production` schema
- Configures `raw_data` volume for data storage

#### **Synthetic Data Generator**
- **Configurable parameters** for trucks, events, and time periods
- **Realistic probability distributions** for event types
- **Time-based patterns** with weekend effects
- **Parquet file output** to Unity Catalog volume

### **Data Processing (`pipelines/`)**

#### **Bronze Layer (4 Streaming Tables)**
- `bronze_trucks` - Raw truck data
- `bronze_truck_cycles` - Raw cycle data
- `bronze_truck_productivity_events` - Raw event data
- `bronze_time_usage_model` - Raw time usage categorization

#### **Silver Layer (4 Materialized Views)**
- Data quality checks and validations
- Business logic and calculated fields
- Time usage model with quality flags
- Performance metrics calculations

#### **Gold Layer (5 Materialized Views)**
- `gold_daily_operational_efficiency` - Daily aggregated metrics
- `gold_truck_performance` - Individual truck performance analysis
- `gold_operational_efficiency_metrics` - Category-based efficiency analysis
- `gold_events_with_time_usage` - Comprehensive event dataset with time usage mapping
- `gold_time_usage_efficiency_summary` - Aggregated efficiency metrics by time periods

### **Visualization (`dashboards/`)**

#### **Demo Dashboard Features**
- **7 Advanced Datasets** leveraging all gold tables
- **8 Interactive Widgets** with professional visualizations
- **Real-time KPI Monitoring** with key performance indicators
- **Efficiency Rating Distribution** (Excellent/Good/Fair/Poor/Critical)
- **Time-based Analysis** (Morning/Afternoon/Evening/Night efficiency)
- **Productivity Loss Identification** with quantified improvement opportunities
- **Truck Performance Leaderboard** with competitive benchmarking

## 📈 Key Insights & Analytics

### **Operational Efficiency Metrics**
- **Daily efficiency trends** over 30-day periods
- **Time-of-day efficiency patterns** for scheduling optimization
- **Event efficiency ratings** with color-coded classifications
- **Productivity loss quantification** in minutes and hours

### **Performance Analysis**
- **Truck performance ranking** with efficiency categories
- **Breakdown and delay pattern analysis** for maintenance planning
- **Event type impact assessment** for improvement prioritization
- **Historical trend analysis** for strategic planning

### **Business Intelligence**
- **ROI quantification** through productivity improvement identification
- **Cost optimization** via targeted improvement investments
- **Resource allocation** based on efficiency patterns
- **Predictive insights** for operational planning

## 🎨 Dashboard Visualizations

### **Executive Summary**
- **KPI Dashboard** with key performance indicators
- **Efficiency trend charts** for historical analysis
- **Performance distribution** with color-coded ratings

### **Operational Analysis**
- **Time-based efficiency** patterns and optimization opportunities
- **Productivity loss heatmaps** for improvement prioritization
- **Truck performance leaderboards** for competitive benchmarking

### **Interactive Features**
- **Drill-down capabilities** from high-level trends to individual events
- **Real-time data updates** with live pipeline processing
- **Filter integration** for time periods and categories
- **Responsive design** for various screen sizes

## 🔍 Data Quality & Governance

### **Quality Constraints**
- **EXPECT constraints** built into table definitions
- **Range validations** for operational metrics
- **Referential integrity** checks between entities
- **Temporal consistency** for event timestamps

### **Data Lineage**
- **Bronze → Silver → Gold** transformation tracking
- **Source data** preservation in bronze layer
- **Quality flags** and validation results
- **Processing timestamps** for audit trails

## 🚀 Advanced Features

### **Time Usage Analysis**
- **Event categorization** with efficiency mapping
- **Productivity classification** (Productive/Non-Productive)
- **Efficiency ratings** (Excellent/Good/Fair/Poor/Critical)
- **Lost productivity quantification** in minutes

### **Real-time Processing**
- **Streaming tables** for append-only data ingestion
- **Materialized views** for efficient transformations
- **Automatic refresh** with new data arrival
- **Exactly-once processing** guarantees

### **Scalable Architecture**
- **Unity Catalog** for data governance and security
- **Lakeflow Pipelines** for declarative data processing
- **Delta Lake** for ACID transactions and versioning
- **Cloud-native** design for enterprise scalability

## 📊 Demo Capabilities

### **Professional Presentation**
- **7-minute demo script** with clear talking points
- **Executive summary** for quick insights
- **Technical deep-dive** for implementation details
- **Business value** demonstration with ROI metrics

### **Interactive Showcase**
- **Live data processing** demonstration
- **Real-time analytics** with streaming updates
- **Drill-down analysis** from trends to individual events
- **Performance benchmarking** with competitive insights

## 🔧 Configuration & Customization

### **Data Generation Parameters**
```python
NUM_TRUCKS = 50                    # Number of trucks
DAYS_TO_GENERATE = 30             # Time period
MIN_EVENTS_PER_DAY = 30           # Minimum events per truck per day
MAX_EVENTS_PER_DAY = 60           # Maximum events per truck per day
PRODUCTIVE_EVENT_PROBABILITY = 0.85  # 85% productive events
BREAKDOWN_PROBABILITY = 0.03      # 3% breakdown events
DELAY_PROBABILITY = 0.12          # 12% delay events
```

### **Pipeline Configuration**
- **Bronze layer** streaming table configurations
- **Silver layer** materialized view definitions
- **Gold layer** analytical table specifications
- **Data quality** constraint definitions

## 📚 Documentation

### **Setup Guides**
- **Unity Catalog Setup** - Initial configuration instructions
- **Data Generation** - Synthetic data creation and parameters
- **Pipeline Deployment** - Lakeflow pipeline configuration
- **Dashboard Import** - Visualization setup and customization

### **Demo Materials**
- **Demo Script** - Professional presentation guide
- **Technical Overview** - Architecture and capabilities
- **Business Value** - ROI and improvement opportunities
- **Implementation Guide** - Production deployment steps

## 🤝 Contributing

### **Development Setup**
1. Clone the repository
2. Set up Databricks workspace with Unity Catalog
3. Install required dependencies from `requirements.txt`
4. Run setup notebooks in order
5. Deploy pipeline and import dashboard

### **Customization**
- **Modify data generation** parameters for different scenarios
- **Extend pipeline** with additional transformations
- **Create custom dashboards** for specific use cases
- **Add new analytics** and insights

## 📄 License

This project is designed for demonstration and educational purposes. Please ensure compliance with your organization's data governance and security policies when deploying to production environments.

## 🆘 Support

For questions, issues, or customization requests:
1. Review the documentation in each notebook
2. Check the demo guides for implementation details
3. Verify Unity Catalog permissions and configurations
4. Ensure all dependencies are properly installed

---

**Built with ❤️ using Databricks, Lakeflow, and Unity Catalog for modern data analytics and operational intelligence.**
