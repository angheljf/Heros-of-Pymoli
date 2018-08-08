# Unit 4: Pandas Assignment
Pandas Assignment in Jupyter Lab

{
 "cells": [
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "### Heroes Of Pymoli Data Analysis\n",
    "\n",
    "#### Background \n",
    "\n",
    "Congratulations! After a lot of hard work in the data munging mines, you've landed a job as Lead Analyst for an independent gaming company. You've been assigned the task of analyzing the data for their most recent fantasy game Heroes of Pymoli.\n",
    "\n",
    "Like many others in its genre, the game is free-to-play, but players are encouraged to purchase optional items that enhance their playing experience. As a first task, the company would like you to generate a report that breaks down the game's purchasing data into meaningful insights.\n",
    "\n",
    "-----\n",
    "\n",
    "#### Observable Trends\n",
    "\n",
    "* Of the 753 active and inactive players, the vast majority are male (87%). There also exists, a smaller, but notable proportion of female players (15%).\n",
    "\n",
    "* Our peak age demographic falls between 20-24 (63.37 %) with secondary groups falling between 15-19 (23.61%) and 25-29 (17.53%).  \n",
    "* The demographic that spends the most money is the 20-24 with 1,114.06 dollars total purchase value. \n",
    "\n",
    "-----\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 1,
   "metadata": {},
   "outputs": [],
   "source": [
    "# Dependencies and Setup\n",
    "import pandas as pd\n",
    "import numpy as np\n",
    "\n",
    "# Raw data file\n",
    "file_to_load = \"Resources/purchase_data.csv\"\n",
    "\n",
    "# Read purchasing file and store into pandas data frame\n",
    "purchase_data = pd.read_csv(file_to_load)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## Player Count"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "* Total Number of Players\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 2,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>Total Players</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>576</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "   Total Players\n",
       "0            576"
      ]
     },
     "execution_count": 2,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# Use the lenght of list of screen names \"SN\", for total players.\n",
    "total_players = len(purchase_data[\"SN\"].value_counts())\n",
    "\n",
    "# Create a data frame with total players named player count\n",
    "player_count = pd.DataFrame({\"Total Players\":[total_players]})\n",
    "player_count"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## Purchasing Analysis (Total)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "* Number of Unique Items\n",
    "\n",
    "\n",
    "* Average Purchase Price\n",
    "\n",
    "\n",
    "* Total Number of Purchases\n",
    "\n",
    "\n",
    "* Total Revenue\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 3,
   "metadata": {
    "scrolled": true
   },
   "outputs": [
    {
     "data": {
      "text/html": [
       "<style  type=\"text/css\" >\n",
       "</style>  \n",
       "<table id=\"T_65be6b3e_9b48_11e8_8a26_d49a20d1630f\" > \n",
       "<thead>    <tr> \n",
       "        <th class=\"blank level0\" ></th> \n",
       "        <th class=\"col_heading level0 col0\" >Number of Unique Items</th> \n",
       "        <th class=\"col_heading level0 col1\" >Average Price</th> \n",
       "        <th class=\"col_heading level0 col2\" >Number of Purchases</th> \n",
       "        <th class=\"col_heading level0 col3\" >Total Revenue</th> \n",
       "    </tr></thead> \n",
       "<tbody>    <tr> \n",
       "        <th id=\"T_65be6b3e_9b48_11e8_8a26_d49a20d1630flevel0_row0\" class=\"row_heading level0 row0\" >0</th> \n",
       "        <td id=\"T_65be6b3e_9b48_11e8_8a26_d49a20d1630frow0_col0\" class=\"data row0 col0\" >183</td> \n",
       "        <td id=\"T_65be6b3e_9b48_11e8_8a26_d49a20d1630frow0_col1\" class=\"data row0 col1\" >$3.05</td> \n",
       "        <td id=\"T_65be6b3e_9b48_11e8_8a26_d49a20d1630frow0_col2\" class=\"data row0 col2\" >780</td> \n",
       "        <td id=\"T_65be6b3e_9b48_11e8_8a26_d49a20d1630frow0_col3\" class=\"data row0 col3\" >$2,379.77</td> \n",
       "    </tr></tbody> \n",
       "</table> "
      ],
      "text/plain": [
       "<pandas.io.formats.style.Styler at 0x10cc60e10>"
      ]
     },
     "execution_count": 3,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# Calculations for unique items, average price, purchase count, and revenue\n",
    "number_of_unique_items = len((purchase_data[\"Item ID\"]).unique())\n",
    "average_price = (purchase_data[\"Price\"]).mean()\n",
    "number_of_purchases = (purchase_data[\"Purchase ID\"]).count()\n",
    "total_revenue = (purchase_data[\"Price\"]).sum()\n",
    "\n",
    "# Create data frame with obtained values\n",
    "summary_df = pd.DataFrame({\"Number of Unique Items\":[number_of_unique_items],\n",
    "                           \"Average Price\":[average_price], \n",
    "                           \"Number of Purchases\": [number_of_purchases], \n",
    "                           \"Total Revenue\": [total_revenue]})\n",
    "\n",
    "# Format with currency style\n",
    "summary_df.style.format({'Average Price':\"${:,.2f}\",\n",
    "                         'Total Revenue': '${:,.2f}'})"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## Gender Demographics"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "* Percentage and Count of Male Players\n",
    "\n",
    "\n",
    "* Percentage and Count of Female Players\n",
    "\n",
    "\n",
    "* Percentage and Count of Other / Non-Disclosed\n",
    "\n",
    "\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 4,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<style  type=\"text/css\" >\n",
       "</style>  \n",
       "<table id=\"T_65d8f618_9b48_11e8_aa10_d49a20d1630f\" > \n",
       "<thead>    <tr> \n",
       "        <th class=\"blank level0\" ></th> \n",
       "        <th class=\"col_heading level0 col0\" >Percentage of Players</th> \n",
       "        <th class=\"col_heading level0 col1\" >Total Count</th> \n",
       "    </tr></thead> \n",
       "<tbody>    <tr> \n",
       "        <th id=\"T_65d8f618_9b48_11e8_aa10_d49a20d1630flevel0_row0\" class=\"row_heading level0 row0\" >Male</th> \n",
       "        <td id=\"T_65d8f618_9b48_11e8_aa10_d49a20d1630frow0_col0\" class=\"data row0 col0\" >113.19</td> \n",
       "        <td id=\"T_65d8f618_9b48_11e8_aa10_d49a20d1630frow0_col1\" class=\"data row0 col1\" >652</td> \n",
       "    </tr>    <tr> \n",
       "        <th id=\"T_65d8f618_9b48_11e8_aa10_d49a20d1630flevel0_row1\" class=\"row_heading level0 row1\" >Female</th> \n",
       "        <td id=\"T_65d8f618_9b48_11e8_aa10_d49a20d1630frow1_col0\" class=\"data row1 col0\" >19.62</td> \n",
       "        <td id=\"T_65d8f618_9b48_11e8_aa10_d49a20d1630frow1_col1\" class=\"data row1 col1\" >113</td> \n",
       "    </tr>    <tr> \n",
       "        <th id=\"T_65d8f618_9b48_11e8_aa10_d49a20d1630flevel0_row2\" class=\"row_heading level0 row2\" >Other / Non-Disclosed</th> \n",
       "        <td id=\"T_65d8f618_9b48_11e8_aa10_d49a20d1630frow2_col0\" class=\"data row2 col0\" >2.60</td> \n",
       "        <td id=\"T_65d8f618_9b48_11e8_aa10_d49a20d1630frow2_col1\" class=\"data row2 col1\" >15</td> \n",
       "    </tr></tbody> \n",
       "</table> "
      ],
      "text/plain": [
       "<pandas.io.formats.style.Styler at 0x10dfd0c18>"
      ]
     },
     "execution_count": 4,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# Group purchase_data by Gender\n",
    "gender_stats = purchase_data.groupby(\"Gender\")\n",
    "\n",
    "# Count the total of screen names \"SN\" by gender\n",
    "total_count_gender = gender_stats.count()[\"SN\"]\n",
    "\n",
    "# Total count by gender and divivde by total players \n",
    "percentage_of_players = total_count_gender / total_players * 100\n",
    "\n",
    "# Create data frame with obtained values\n",
    "gender_demographics = pd.DataFrame({\"Percentage of Players\": percentage_of_players, \"Total Count\": total_count_gender})\n",
    "\n",
    "# Format the data frame with no index name in the corner\n",
    "gender_demographics.index.name = None\n",
    "\n",
    "# Format the values sorted by total count in descending order, and two decimal places for the percentage\n",
    "gender_demographics.sort_values([\"Total Count\"], ascending = False).style.format({\"Percentage of Players\":\"{:.2f}\"})\n",
    "\n",
    "\n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "\n",
    "## Purchasing Analysis (Gender)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "* The below each broken by gender\n",
    "\n",
    "  * Purchase Count\n",
    "  \n",
    "  * Average Purchase Price\n",
    "  \n",
    "  * Total Purchase Value\n",
    "  \n",
    "  * Average Purchase Total per Person by Gender"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 5,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<style  type=\"text/css\" >\n",
       "</style>  \n",
       "<table id=\"T_65dc17f6_9b48_11e8_811d_d49a20d1630f\" > \n",
       "<thead>    <tr> \n",
       "        <th class=\"blank level0\" ></th> \n",
       "        <th class=\"col_heading level0 col0\" >Purchase Count</th> \n",
       "        <th class=\"col_heading level0 col1\" >Average Purchase Price</th> \n",
       "        <th class=\"col_heading level0 col2\" >Average Purchase Value</th> \n",
       "        <th class=\"col_heading level0 col3\" >Avg Purchase Total per Person</th> \n",
       "    </tr>    <tr> \n",
       "        <th class=\"index_name level0\" >Gender</th> \n",
       "        <th class=\"blank\" ></th> \n",
       "        <th class=\"blank\" ></th> \n",
       "        <th class=\"blank\" ></th> \n",
       "        <th class=\"blank\" ></th> \n",
       "    </tr></thead> \n",
       "<tbody>    <tr> \n",
       "        <th id=\"T_65dc17f6_9b48_11e8_811d_d49a20d1630flevel0_row0\" class=\"row_heading level0 row0\" >Female</th> \n",
       "        <td id=\"T_65dc17f6_9b48_11e8_811d_d49a20d1630frow0_col0\" class=\"data row0 col0\" >113</td> \n",
       "        <td id=\"T_65dc17f6_9b48_11e8_811d_d49a20d1630frow0_col1\" class=\"data row0 col1\" >$3.20</td> \n",
       "        <td id=\"T_65dc17f6_9b48_11e8_811d_d49a20d1630frow0_col2\" class=\"data row0 col2\" >$361.94</td> \n",
       "        <td id=\"T_65dc17f6_9b48_11e8_811d_d49a20d1630frow0_col3\" class=\"data row0 col3\" >$3.20</td> \n",
       "    </tr>    <tr> \n",
       "        <th id=\"T_65dc17f6_9b48_11e8_811d_d49a20d1630flevel0_row1\" class=\"row_heading level0 row1\" >Male</th> \n",
       "        <td id=\"T_65dc17f6_9b48_11e8_811d_d49a20d1630frow1_col0\" class=\"data row1 col0\" >652</td> \n",
       "        <td id=\"T_65dc17f6_9b48_11e8_811d_d49a20d1630frow1_col1\" class=\"data row1 col1\" >$3.02</td> \n",
       "        <td id=\"T_65dc17f6_9b48_11e8_811d_d49a20d1630frow1_col2\" class=\"data row1 col2\" >$1,967.64</td> \n",
       "        <td id=\"T_65dc17f6_9b48_11e8_811d_d49a20d1630frow1_col3\" class=\"data row1 col3\" >$3.02</td> \n",
       "    </tr>    <tr> \n",
       "        <th id=\"T_65dc17f6_9b48_11e8_811d_d49a20d1630flevel0_row2\" class=\"row_heading level0 row2\" >Other / Non-Disclosed</th> \n",
       "        <td id=\"T_65dc17f6_9b48_11e8_811d_d49a20d1630frow2_col0\" class=\"data row2 col0\" >15</td> \n",
       "        <td id=\"T_65dc17f6_9b48_11e8_811d_d49a20d1630frow2_col1\" class=\"data row2 col1\" >$3.35</td> \n",
       "        <td id=\"T_65dc17f6_9b48_11e8_811d_d49a20d1630frow2_col2\" class=\"data row2 col2\" >$50.19</td> \n",
       "        <td id=\"T_65dc17f6_9b48_11e8_811d_d49a20d1630frow2_col3\" class=\"data row2 col3\" >$3.35</td> \n",
       "    </tr></tbody> \n",
       "</table> "
      ],
      "text/plain": [
       "<pandas.io.formats.style.Styler at 0x10e092668>"
      ]
     },
     "execution_count": 5,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# Count the total purchases by gender \n",
    "purchase_count = gender_stats[\"Purchase ID\"].count()\n",
    "\n",
    "# Average purchase prices by gender\n",
    "avg_purchase_price = gender_stats[\"Price\"].mean()\n",
    "\n",
    "# Average purchase total by gender \n",
    "avg_purchase_total = gender_stats[\"Price\"].sum()\n",
    "\n",
    "# Average purchase total by gender divivded by purchase count \n",
    "avg_purchase_per_person = avg_purchase_total/purchase_count\n",
    "\n",
    "# Create data frame with obtained values \n",
    "gender_demographics = pd.DataFrame({\"Purchase Count\": purchase_count, \n",
    "                                    \"Average Purchase Price\": avg_purchase_price,\n",
    "                                    \"Average Purchase Value\":avg_purchase_total,\n",
    "                                    \"Avg Purchase Total per Person\": avg_purchase_per_person})\n",
    "\n",
    "# Provide index in top left as \"Gender\"\n",
    "gender_demographics.index.name = \"Gender\"\n",
    "\n",
    "# Format with currency style\n",
    "gender_demographics.style.format({\"Average Purchase Value\":\"${:,.2f}\",\n",
    "                                  \"Average Purchase Price\":\"${:,.2f}\",\n",
    "                                  \"Avg Purchase Total per Person\":\"${:,.2f}\"})\n",
    "\n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## Age Demographics"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "* The below each broken into bins of 4 years (i.e. &lt;10, 10-14, 15-19, etc.)\n",
    "\n",
    "  * Percentage of Players\n",
    "  \n",
    "  * Total Count \n",
    "\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 6,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<style  type=\"text/css\" >\n",
       "</style>  \n",
       "<table id=\"T_65e0d570_9b48_11e8_bc53_d49a20d1630f\" > \n",
       "<thead>    <tr> \n",
       "        <th class=\"blank level0\" ></th> \n",
       "        <th class=\"col_heading level0 col0\" >Percentage of Players</th> \n",
       "        <th class=\"col_heading level0 col1\" >Total Count</th> \n",
       "    </tr></thead> \n",
       "<tbody>    <tr> \n",
       "        <th id=\"T_65e0d570_9b48_11e8_bc53_d49a20d1630flevel0_row0\" class=\"row_heading level0 row0\" ><10</th> \n",
       "        <td id=\"T_65e0d570_9b48_11e8_bc53_d49a20d1630frow0_col0\" class=\"data row0 col0\" >3.99</td> \n",
       "        <td id=\"T_65e0d570_9b48_11e8_bc53_d49a20d1630frow0_col1\" class=\"data row0 col1\" >23</td> \n",
       "    </tr>    <tr> \n",
       "        <th id=\"T_65e0d570_9b48_11e8_bc53_d49a20d1630flevel0_row1\" class=\"row_heading level0 row1\" >10-14</th> \n",
       "        <td id=\"T_65e0d570_9b48_11e8_bc53_d49a20d1630frow1_col0\" class=\"data row1 col0\" >4.86</td> \n",
       "        <td id=\"T_65e0d570_9b48_11e8_bc53_d49a20d1630frow1_col1\" class=\"data row1 col1\" >28</td> \n",
       "    </tr>    <tr> \n",
       "        <th id=\"T_65e0d570_9b48_11e8_bc53_d49a20d1630flevel0_row2\" class=\"row_heading level0 row2\" >15-19</th> \n",
       "        <td id=\"T_65e0d570_9b48_11e8_bc53_d49a20d1630frow2_col0\" class=\"data row2 col0\" >23.61</td> \n",
       "        <td id=\"T_65e0d570_9b48_11e8_bc53_d49a20d1630frow2_col1\" class=\"data row2 col1\" >136</td> \n",
       "    </tr>    <tr> \n",
       "        <th id=\"T_65e0d570_9b48_11e8_bc53_d49a20d1630flevel0_row3\" class=\"row_heading level0 row3\" >20-24</th> \n",
       "        <td id=\"T_65e0d570_9b48_11e8_bc53_d49a20d1630frow3_col0\" class=\"data row3 col0\" >63.37</td> \n",
       "        <td id=\"T_65e0d570_9b48_11e8_bc53_d49a20d1630frow3_col1\" class=\"data row3 col1\" >365</td> \n",
       "    </tr>    <tr> \n",
       "        <th id=\"T_65e0d570_9b48_11e8_bc53_d49a20d1630flevel0_row4\" class=\"row_heading level0 row4\" >25-29</th> \n",
       "        <td id=\"T_65e0d570_9b48_11e8_bc53_d49a20d1630frow4_col0\" class=\"data row4 col0\" >17.53</td> \n",
       "        <td id=\"T_65e0d570_9b48_11e8_bc53_d49a20d1630frow4_col1\" class=\"data row4 col1\" >101</td> \n",
       "    </tr>    <tr> \n",
       "        <th id=\"T_65e0d570_9b48_11e8_bc53_d49a20d1630flevel0_row5\" class=\"row_heading level0 row5\" >30-34</th> \n",
       "        <td id=\"T_65e0d570_9b48_11e8_bc53_d49a20d1630frow5_col0\" class=\"data row5 col0\" >12.67</td> \n",
       "        <td id=\"T_65e0d570_9b48_11e8_bc53_d49a20d1630frow5_col1\" class=\"data row5 col1\" >73</td> \n",
       "    </tr>    <tr> \n",
       "        <th id=\"T_65e0d570_9b48_11e8_bc53_d49a20d1630flevel0_row6\" class=\"row_heading level0 row6\" >35-39</th> \n",
       "        <td id=\"T_65e0d570_9b48_11e8_bc53_d49a20d1630frow6_col0\" class=\"data row6 col0\" >7.12</td> \n",
       "        <td id=\"T_65e0d570_9b48_11e8_bc53_d49a20d1630frow6_col1\" class=\"data row6 col1\" >41</td> \n",
       "    </tr>    <tr> \n",
       "        <th id=\"T_65e0d570_9b48_11e8_bc53_d49a20d1630flevel0_row7\" class=\"row_heading level0 row7\" >40+</th> \n",
       "        <td id=\"T_65e0d570_9b48_11e8_bc53_d49a20d1630frow7_col0\" class=\"data row7 col0\" >2.26</td> \n",
       "        <td id=\"T_65e0d570_9b48_11e8_bc53_d49a20d1630frow7_col1\" class=\"data row7 col1\" >13</td> \n",
       "    </tr></tbody> \n",
       "</table> "
      ],
      "text/plain": [
       "<pandas.io.formats.style.Styler at 0x10e0d9ba8>"
      ]
     },
     "execution_count": 6,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# Establish bins for ages\n",
    "age_bins = [0, 9.90, 14.90, 19.90, 24.90, 29.90, 34.90, 39.90, 99999]\n",
    "group_names = [\"<10\", \"10-14\", \"15-19\", \"20-24\", \"25-29\", \"30-34\", \"35-39\", \"40+\"]\n",
    "\n",
    "# Segment and sort age values into bins established above\n",
    "purchase_data[\"Age Group\"] = pd.cut(purchase_data[\"Age\"],age_bins, labels=group_names)\n",
    "purchase_data\n",
    "\n",
    "# Create new data frame with the added \"Age Group\" and group it\n",
    "age_grouped = purchase_data.groupby(\"Age Group\")\n",
    "\n",
    "# Count total players by age category\n",
    "total_count_age = age_grouped[\"Age\"].count()\n",
    "\n",
    "# Calculate percentages by age category \n",
    "percentage_by_age = (age_grouped.count()[\"Age\"]/total_players) * 100\n",
    "\n",
    "# Create data frame with obtained values\n",
    "age_demographics = pd.DataFrame({\"Percentage of Players\": percentage_by_age, \"Total Count\": total_count_age})\n",
    "\n",
    "# Format the data frame with no index name in the corner\n",
    "age_demographics.index.name = None\n",
    "\n",
    "# Format percentage with two decimal places \n",
    "age_demographics.style.format({\"Percentage of Players\":\"{:,.2f}\"})\n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## Purchasing Analysis (Age)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "* The below each broken into bins of 4 years (i.e. &lt;10, 10-14, 15-19, etc.)\n",
    "\n",
    "  * Purchase Count\n",
    "  \n",
    "  * Average Purchase Price\n",
    "  \n",
    "  * Total Purchase Value\n",
    "  \n",
    "  * Average Purchase Total per Person by Age Group\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 7,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<style  type=\"text/css\" >\n",
       "</style>  \n",
       "<table id=\"T_65e390a8_9b48_11e8_a83f_d49a20d1630f\" > \n",
       "<thead>    <tr> \n",
       "        <th class=\"blank level0\" ></th> \n",
       "        <th class=\"col_heading level0 col0\" >Purchase Count</th> \n",
       "        <th class=\"col_heading level0 col1\" >Average Purchase Price</th> \n",
       "        <th class=\"col_heading level0 col2\" >Total Purchase Value</th> \n",
       "        <th class=\"col_heading level0 col3\" >Average Purchase Total per Person</th> \n",
       "    </tr></thead> \n",
       "<tbody>    <tr> \n",
       "        <th id=\"T_65e390a8_9b48_11e8_a83f_d49a20d1630flevel0_row0\" class=\"row_heading level0 row0\" ><10</th> \n",
       "        <td id=\"T_65e390a8_9b48_11e8_a83f_d49a20d1630frow0_col0\" class=\"data row0 col0\" >23</td> \n",
       "        <td id=\"T_65e390a8_9b48_11e8_a83f_d49a20d1630frow0_col1\" class=\"data row0 col1\" >$3.35</td> \n",
       "        <td id=\"T_65e390a8_9b48_11e8_a83f_d49a20d1630frow0_col2\" class=\"data row0 col2\" >$77.13</td> \n",
       "        <td id=\"T_65e390a8_9b48_11e8_a83f_d49a20d1630frow0_col3\" class=\"data row0 col3\" >$3.35</td> \n",
       "    </tr>    <tr> \n",
       "        <th id=\"T_65e390a8_9b48_11e8_a83f_d49a20d1630flevel0_row1\" class=\"row_heading level0 row1\" >10-14</th> \n",
       "        <td id=\"T_65e390a8_9b48_11e8_a83f_d49a20d1630frow1_col0\" class=\"data row1 col0\" >28</td> \n",
       "        <td id=\"T_65e390a8_9b48_11e8_a83f_d49a20d1630frow1_col1\" class=\"data row1 col1\" >$2.96</td> \n",
       "        <td id=\"T_65e390a8_9b48_11e8_a83f_d49a20d1630frow1_col2\" class=\"data row1 col2\" >$82.78</td> \n",
       "        <td id=\"T_65e390a8_9b48_11e8_a83f_d49a20d1630frow1_col3\" class=\"data row1 col3\" >$2.96</td> \n",
       "    </tr>    <tr> \n",
       "        <th id=\"T_65e390a8_9b48_11e8_a83f_d49a20d1630flevel0_row2\" class=\"row_heading level0 row2\" >15-19</th> \n",
       "        <td id=\"T_65e390a8_9b48_11e8_a83f_d49a20d1630frow2_col0\" class=\"data row2 col0\" >136</td> \n",
       "        <td id=\"T_65e390a8_9b48_11e8_a83f_d49a20d1630frow2_col1\" class=\"data row2 col1\" >$3.04</td> \n",
       "        <td id=\"T_65e390a8_9b48_11e8_a83f_d49a20d1630frow2_col2\" class=\"data row2 col2\" >$412.89</td> \n",
       "        <td id=\"T_65e390a8_9b48_11e8_a83f_d49a20d1630frow2_col3\" class=\"data row2 col3\" >$3.04</td> \n",
       "    </tr>    <tr> \n",
       "        <th id=\"T_65e390a8_9b48_11e8_a83f_d49a20d1630flevel0_row3\" class=\"row_heading level0 row3\" >20-24</th> \n",
       "        <td id=\"T_65e390a8_9b48_11e8_a83f_d49a20d1630frow3_col0\" class=\"data row3 col0\" >365</td> \n",
       "        <td id=\"T_65e390a8_9b48_11e8_a83f_d49a20d1630frow3_col1\" class=\"data row3 col1\" >$3.05</td> \n",
       "        <td id=\"T_65e390a8_9b48_11e8_a83f_d49a20d1630frow3_col2\" class=\"data row3 col2\" >$1,114.06</td> \n",
       "        <td id=\"T_65e390a8_9b48_11e8_a83f_d49a20d1630frow3_col3\" class=\"data row3 col3\" >$3.05</td> \n",
       "    </tr>    <tr> \n",
       "        <th id=\"T_65e390a8_9b48_11e8_a83f_d49a20d1630flevel0_row4\" class=\"row_heading level0 row4\" >25-29</th> \n",
       "        <td id=\"T_65e390a8_9b48_11e8_a83f_d49a20d1630frow4_col0\" class=\"data row4 col0\" >101</td> \n",
       "        <td id=\"T_65e390a8_9b48_11e8_a83f_d49a20d1630frow4_col1\" class=\"data row4 col1\" >$2.90</td> \n",
       "        <td id=\"T_65e390a8_9b48_11e8_a83f_d49a20d1630frow4_col2\" class=\"data row4 col2\" >$293.00</td> \n",
       "        <td id=\"T_65e390a8_9b48_11e8_a83f_d49a20d1630frow4_col3\" class=\"data row4 col3\" >$2.90</td> \n",
       "    </tr>    <tr> \n",
       "        <th id=\"T_65e390a8_9b48_11e8_a83f_d49a20d1630flevel0_row5\" class=\"row_heading level0 row5\" >30-34</th> \n",
       "        <td id=\"T_65e390a8_9b48_11e8_a83f_d49a20d1630frow5_col0\" class=\"data row5 col0\" >73</td> \n",
       "        <td id=\"T_65e390a8_9b48_11e8_a83f_d49a20d1630frow5_col1\" class=\"data row5 col1\" >$2.93</td> \n",
       "        <td id=\"T_65e390a8_9b48_11e8_a83f_d49a20d1630frow5_col2\" class=\"data row5 col2\" >$214.00</td> \n",
       "        <td id=\"T_65e390a8_9b48_11e8_a83f_d49a20d1630frow5_col3\" class=\"data row5 col3\" >$2.93</td> \n",
       "    </tr>    <tr> \n",
       "        <th id=\"T_65e390a8_9b48_11e8_a83f_d49a20d1630flevel0_row6\" class=\"row_heading level0 row6\" >35-39</th> \n",
       "        <td id=\"T_65e390a8_9b48_11e8_a83f_d49a20d1630frow6_col0\" class=\"data row6 col0\" >41</td> \n",
       "        <td id=\"T_65e390a8_9b48_11e8_a83f_d49a20d1630frow6_col1\" class=\"data row6 col1\" >$3.60</td> \n",
       "        <td id=\"T_65e390a8_9b48_11e8_a83f_d49a20d1630frow6_col2\" class=\"data row6 col2\" >$147.67</td> \n",
       "        <td id=\"T_65e390a8_9b48_11e8_a83f_d49a20d1630frow6_col3\" class=\"data row6 col3\" >$3.60</td> \n",
       "    </tr>    <tr> \n",
       "        <th id=\"T_65e390a8_9b48_11e8_a83f_d49a20d1630flevel0_row7\" class=\"row_heading level0 row7\" >40+</th> \n",
       "        <td id=\"T_65e390a8_9b48_11e8_a83f_d49a20d1630frow7_col0\" class=\"data row7 col0\" >13</td> \n",
       "        <td id=\"T_65e390a8_9b48_11e8_a83f_d49a20d1630frow7_col1\" class=\"data row7 col1\" >$2.94</td> \n",
       "        <td id=\"T_65e390a8_9b48_11e8_a83f_d49a20d1630frow7_col2\" class=\"data row7 col2\" >$38.24</td> \n",
       "        <td id=\"T_65e390a8_9b48_11e8_a83f_d49a20d1630frow7_col3\" class=\"data row7 col3\" >$2.94</td> \n",
       "    </tr></tbody> \n",
       "</table> "
      ],
      "text/plain": [
       "<pandas.io.formats.style.Styler at 0x10e0d9518>"
      ]
     },
     "execution_count": 7,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# Count purchases by age group\n",
    "purchase_count_age = age_grouped[\"Purchase ID\"].count()\n",
    "\n",
    "# Obtain average purchase price by age group \n",
    "avg_purchase_price_age = age_grouped[\"Price\"].mean()\n",
    "\n",
    "# Calculate total purchase value by age group \n",
    "total_purchase_value = age_grouped[\"Price\"].sum()\n",
    "\n",
    "# Calculate the average purchase per person in the age group \n",
    "avg_purchase_per_person_age = total_purchase_value/purchase_count_age\n",
    "\n",
    "# Create data frame with obtained values\n",
    "age_demographics = pd.DataFrame({\"Purchase Count\": purchase_count_age,\n",
    "                                 \"Average Purchase Price\": avg_purchase_price_age,\n",
    "                                 \"Total Purchase Value\":total_purchase_value,\n",
    "                                 \"Average Purchase Total per Person\": avg_purchase_per_person_age})\n",
    "\n",
    "# Format the data frame with no index name in the corner\n",
    "age_demographics.index.name = None\n",
    "\n",
    "# Format with currency style\n",
    "age_demographics.style.format({\"Average Purchase Price\":\"${:,.2f}\",\n",
    "                               \"Total Purchase Value\":\"${:,.2f}\",\n",
    "                               \"Average Purchase Total per Person\":\"${:,.2f}\"})\n",
    "\n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## Top Spenders"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "* Identify the the top 5 spenders in the game by total purchase value, then list (in a table):\n",
    "\n",
    "  * SN(screen name)\n",
    "  \n",
    "  * Purchase Count\n",
    "  \n",
    "  * Average Purchase Price\n",
    "  \n",
    "  * Total Purchase Value\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 8,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<style  type=\"text/css\" >\n",
       "</style>  \n",
       "<table id=\"T_65e7844c_9b48_11e8_869e_d49a20d1630f\" > \n",
       "<thead>    <tr> \n",
       "        <th class=\"blank level0\" ></th> \n",
       "        <th class=\"col_heading level0 col0\" >Purchase Count</th> \n",
       "        <th class=\"col_heading level0 col1\" >Average Purchase Price</th> \n",
       "        <th class=\"col_heading level0 col2\" >Total Purchase Value</th> \n",
       "    </tr>    <tr> \n",
       "        <th class=\"index_name level0\" >SN</th> \n",
       "        <th class=\"blank\" ></th> \n",
       "        <th class=\"blank\" ></th> \n",
       "        <th class=\"blank\" ></th> \n",
       "    </tr></thead> \n",
       "<tbody>    <tr> \n",
       "        <th id=\"T_65e7844c_9b48_11e8_869e_d49a20d1630flevel0_row0\" class=\"row_heading level0 row0\" >Lisosia93</th> \n",
       "        <td id=\"T_65e7844c_9b48_11e8_869e_d49a20d1630frow0_col0\" class=\"data row0 col0\" >5</td> \n",
       "        <td id=\"T_65e7844c_9b48_11e8_869e_d49a20d1630frow0_col1\" class=\"data row0 col1\" >$3.79</td> \n",
       "        <td id=\"T_65e7844c_9b48_11e8_869e_d49a20d1630frow0_col2\" class=\"data row0 col2\" >$18.96</td> \n",
       "    </tr>    <tr> \n",
       "        <th id=\"T_65e7844c_9b48_11e8_869e_d49a20d1630flevel0_row1\" class=\"row_heading level0 row1\" >Idastidru52</th> \n",
       "        <td id=\"T_65e7844c_9b48_11e8_869e_d49a20d1630frow1_col0\" class=\"data row1 col0\" >4</td> \n",
       "        <td id=\"T_65e7844c_9b48_11e8_869e_d49a20d1630frow1_col1\" class=\"data row1 col1\" >$3.86</td> \n",
       "        <td id=\"T_65e7844c_9b48_11e8_869e_d49a20d1630frow1_col2\" class=\"data row1 col2\" >$15.45</td> \n",
       "    </tr>    <tr> \n",
       "        <th id=\"T_65e7844c_9b48_11e8_869e_d49a20d1630flevel0_row2\" class=\"row_heading level0 row2\" >Chamjask73</th> \n",
       "        <td id=\"T_65e7844c_9b48_11e8_869e_d49a20d1630frow2_col0\" class=\"data row2 col0\" >3</td> \n",
       "        <td id=\"T_65e7844c_9b48_11e8_869e_d49a20d1630frow2_col1\" class=\"data row2 col1\" >$4.61</td> \n",
       "        <td id=\"T_65e7844c_9b48_11e8_869e_d49a20d1630frow2_col2\" class=\"data row2 col2\" >$13.83</td> \n",
       "    </tr>    <tr> \n",
       "        <th id=\"T_65e7844c_9b48_11e8_869e_d49a20d1630flevel0_row3\" class=\"row_heading level0 row3\" >Iral74</th> \n",
       "        <td id=\"T_65e7844c_9b48_11e8_869e_d49a20d1630frow3_col0\" class=\"data row3 col0\" >4</td> \n",
       "        <td id=\"T_65e7844c_9b48_11e8_869e_d49a20d1630frow3_col1\" class=\"data row3 col1\" >$3.40</td> \n",
       "        <td id=\"T_65e7844c_9b48_11e8_869e_d49a20d1630frow3_col2\" class=\"data row3 col2\" >$13.62</td> \n",
       "    </tr>    <tr> \n",
       "        <th id=\"T_65e7844c_9b48_11e8_869e_d49a20d1630flevel0_row4\" class=\"row_heading level0 row4\" >Iskadarya95</th> \n",
       "        <td id=\"T_65e7844c_9b48_11e8_869e_d49a20d1630frow4_col0\" class=\"data row4 col0\" >3</td> \n",
       "        <td id=\"T_65e7844c_9b48_11e8_869e_d49a20d1630frow4_col1\" class=\"data row4 col1\" >$4.37</td> \n",
       "        <td id=\"T_65e7844c_9b48_11e8_869e_d49a20d1630frow4_col2\" class=\"data row4 col2\" >$13.10</td> \n",
       "    </tr></tbody> \n",
       "</table> "
      ],
      "text/plain": [
       "<pandas.io.formats.style.Styler at 0x10e0eb358>"
      ]
     },
     "execution_count": 8,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# Group purchase data by screen names\n",
    "spender_stats = purchase_data.groupby(\"SN\")\n",
    "\n",
    "# Count the total purchases by name\n",
    "purchase_count_spender = spender_stats[\"Purchase ID\"].count()\n",
    "\n",
    "# Calculate the average purchase by name \n",
    "avg_purchase_price_spender = spender_stats[\"Price\"].mean()\n",
    "\n",
    "# Calculate purchase total \n",
    "purchase_total_spender = spender_stats[\"Price\"].sum()\n",
    "\n",
    "# Create data frame with obtained values\n",
    "top_spenders = pd.DataFrame({\"Purchase Count\": purchase_count_spender,\n",
    "                             \"Average Purchase Price\": avg_purchase_price_spender,\n",
    "                             \"Total Purchase Value\":purchase_total_spender})\n",
    "\n",
    "# Sort in descending order to obtain top 5 spender names \n",
    "formatted_spenders = top_spenders.sort_values([\"Total Purchase Value\"], ascending=False).head()\n",
    "\n",
    "# Format with currency style\n",
    "formatted_spenders.style.format({\"Average Purchase Total\":\"${:,.2f}\",\n",
    "                                 \"Average Purchase Price\":\"${:,.2f}\", \n",
    "                                 \"Total Purchase Value\":\"${:,.2f}\"})\n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## Most Popular Items"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "* Top 5 most popular items by purchase count:\n",
    "\n",
    "  * Item ID\n",
    "  \n",
    "  * Item Name\n",
    "  \n",
    "  * Purchase Count\n",
    "  \n",
    "  * Item Price\n",
    "  \n",
    "  * Total Purchase Value"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 9,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<style  type=\"text/css\" >\n",
       "</style>  \n",
       "<table id=\"T_65eb56c6_9b48_11e8_bd67_d49a20d1630f\" > \n",
       "<thead>    <tr> \n",
       "        <th class=\"blank\" ></th> \n",
       "        <th class=\"blank level0\" ></th> \n",
       "        <th class=\"col_heading level0 col0\" >Purchase Count</th> \n",
       "        <th class=\"col_heading level0 col1\" >Item Price</th> \n",
       "        <th class=\"col_heading level0 col2\" >Total Purchase Value</th> \n",
       "    </tr>    <tr> \n",
       "        <th class=\"index_name level0\" >Item ID</th> \n",
       "        <th class=\"index_name level1\" >Item Name</th> \n",
       "        <th class=\"blank\" ></th> \n",
       "        <th class=\"blank\" ></th> \n",
       "        <th class=\"blank\" ></th> \n",
       "    </tr></thead> \n",
       "<tbody>    <tr> \n",
       "        <th id=\"T_65eb56c6_9b48_11e8_bd67_d49a20d1630flevel0_row0\" class=\"row_heading level0 row0\" >178</th> \n",
       "        <th id=\"T_65eb56c6_9b48_11e8_bd67_d49a20d1630flevel1_row0\" class=\"row_heading level1 row0\" >Oathbreaker, Last Hope of the Breaking Storm</th> \n",
       "        <td id=\"T_65eb56c6_9b48_11e8_bd67_d49a20d1630frow0_col0\" class=\"data row0 col0\" >12</td> \n",
       "        <td id=\"T_65eb56c6_9b48_11e8_bd67_d49a20d1630frow0_col1\" class=\"data row0 col1\" >$4.23</td> \n",
       "        <td id=\"T_65eb56c6_9b48_11e8_bd67_d49a20d1630frow0_col2\" class=\"data row0 col2\" >$50.76</td> \n",
       "    </tr>    <tr> \n",
       "        <th id=\"T_65eb56c6_9b48_11e8_bd67_d49a20d1630flevel0_row1\" class=\"row_heading level0 row1\" >145</th> \n",
       "        <th id=\"T_65eb56c6_9b48_11e8_bd67_d49a20d1630flevel1_row1\" class=\"row_heading level1 row1\" >Fiery Glass Crusader</th> \n",
       "        <td id=\"T_65eb56c6_9b48_11e8_bd67_d49a20d1630frow1_col0\" class=\"data row1 col0\" >9</td> \n",
       "        <td id=\"T_65eb56c6_9b48_11e8_bd67_d49a20d1630frow1_col1\" class=\"data row1 col1\" >$4.58</td> \n",
       "        <td id=\"T_65eb56c6_9b48_11e8_bd67_d49a20d1630frow1_col2\" class=\"data row1 col2\" >$41.22</td> \n",
       "    </tr>    <tr> \n",
       "        <th id=\"T_65eb56c6_9b48_11e8_bd67_d49a20d1630flevel0_row2\" class=\"row_heading level0 row2\" >108</th> \n",
       "        <th id=\"T_65eb56c6_9b48_11e8_bd67_d49a20d1630flevel1_row2\" class=\"row_heading level1 row2\" >Extraction, Quickblade Of Trembling Hands</th> \n",
       "        <td id=\"T_65eb56c6_9b48_11e8_bd67_d49a20d1630frow2_col0\" class=\"data row2 col0\" >9</td> \n",
       "        <td id=\"T_65eb56c6_9b48_11e8_bd67_d49a20d1630frow2_col1\" class=\"data row2 col1\" >$3.53</td> \n",
       "        <td id=\"T_65eb56c6_9b48_11e8_bd67_d49a20d1630frow2_col2\" class=\"data row2 col2\" >$31.77</td> \n",
       "    </tr>    <tr> \n",
       "        <th id=\"T_65eb56c6_9b48_11e8_bd67_d49a20d1630flevel0_row3\" class=\"row_heading level0 row3\" >82</th> \n",
       "        <th id=\"T_65eb56c6_9b48_11e8_bd67_d49a20d1630flevel1_row3\" class=\"row_heading level1 row3\" >Nirvana</th> \n",
       "        <td id=\"T_65eb56c6_9b48_11e8_bd67_d49a20d1630frow3_col0\" class=\"data row3 col0\" >9</td> \n",
       "        <td id=\"T_65eb56c6_9b48_11e8_bd67_d49a20d1630frow3_col1\" class=\"data row3 col1\" >$4.90</td> \n",
       "        <td id=\"T_65eb56c6_9b48_11e8_bd67_d49a20d1630frow3_col2\" class=\"data row3 col2\" >$44.10</td> \n",
       "    </tr>    <tr> \n",
       "        <th id=\"T_65eb56c6_9b48_11e8_bd67_d49a20d1630flevel0_row4\" class=\"row_heading level0 row4\" >19</th> \n",
       "        <th id=\"T_65eb56c6_9b48_11e8_bd67_d49a20d1630flevel1_row4\" class=\"row_heading level1 row4\" >Pursuit, Cudgel of Necromancy</th> \n",
       "        <td id=\"T_65eb56c6_9b48_11e8_bd67_d49a20d1630frow4_col0\" class=\"data row4 col0\" >8</td> \n",
       "        <td id=\"T_65eb56c6_9b48_11e8_bd67_d49a20d1630frow4_col1\" class=\"data row4 col1\" >$1.02</td> \n",
       "        <td id=\"T_65eb56c6_9b48_11e8_bd67_d49a20d1630frow4_col2\" class=\"data row4 col2\" >$8.16</td> \n",
       "    </tr></tbody> \n",
       "</table> "
      ],
      "text/plain": [
       "<pandas.io.formats.style.Styler at 0x10e0ebc88>"
      ]
     },
     "execution_count": 9,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# Create new data frame with items related information \n",
    "items = purchase_data[[\"Item ID\", \"Item Name\", \"Price\"]]\n",
    "\n",
    "# Group the item data by item id and item name \n",
    "item_stats = items.groupby([\"Item ID\",\"Item Name\"])\n",
    "\n",
    "# Count the number of times an item has been purchased \n",
    "purchase_count_item = item_stats[\"Price\"].count()\n",
    "\n",
    "# Calcualte the purchase value per item \n",
    "purchase_value = (item_stats[\"Price\"].sum()) \n",
    "\n",
    "# Find individual item price\n",
    "item_price = purchase_value/purchase_count_item\n",
    "\n",
    "# Create data frame with obtained values\n",
    "most_popular_items = pd.DataFrame({\"Purchase Count\": purchase_count_item, \n",
    "                                   \"Item Price\": item_price,\n",
    "                                   \"Total Purchase Value\":purchase_value})\n",
    "\n",
    "# Sort in descending order to obtain top spender names and provide top 5 item names\n",
    "popular_formatted = most_popular_items.sort_values([\"Purchase Count\"], ascending=False).head()\n",
    "\n",
    "# Format with currency style\n",
    "popular_formatted.style.format({\"Item Price\":\"${:,.2f}\",\n",
    "                                \"Total Purchase Value\":\"${:,.2f}\"})"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## Most Profitable Items"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "* Top 5 most profitable items by total purchase value:\n",
    "\n",
    "  * Item ID\n",
    "  \n",
    "  * Item Name\n",
    "  \n",
    "  * Purchase Count\n",
    "  \n",
    "  * Item Price\n",
    "  \n",
    "  * Total Purchase Value"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 10,
   "metadata": {
    "scrolled": true
   },
   "outputs": [
    {
     "data": {
      "text/html": [
       "<style  type=\"text/css\" >\n",
       "</style>  \n",
       "<table id=\"T_65edfd18_9b48_11e8_96aa_d49a20d1630f\" > \n",
       "<thead>    <tr> \n",
       "        <th class=\"blank\" ></th> \n",
       "        <th class=\"blank level0\" ></th> \n",
       "        <th class=\"col_heading level0 col0\" >Purchase Count</th> \n",
       "        <th class=\"col_heading level0 col1\" >Item Price</th> \n",
       "        <th class=\"col_heading level0 col2\" >Total Purchase Value</th> \n",
       "    </tr>    <tr> \n",
       "        <th class=\"index_name level0\" >Item ID</th> \n",
       "        <th class=\"index_name level1\" >Item Name</th> \n",
       "        <th class=\"blank\" ></th> \n",
       "        <th class=\"blank\" ></th> \n",
       "        <th class=\"blank\" ></th> \n",
       "    </tr></thead> \n",
       "<tbody>    <tr> \n",
       "        <th id=\"T_65edfd18_9b48_11e8_96aa_d49a20d1630flevel0_row0\" class=\"row_heading level0 row0\" >178</th> \n",
       "        <th id=\"T_65edfd18_9b48_11e8_96aa_d49a20d1630flevel1_row0\" class=\"row_heading level1 row0\" >Oathbreaker, Last Hope of the Breaking Storm</th> \n",
       "        <td id=\"T_65edfd18_9b48_11e8_96aa_d49a20d1630frow0_col0\" class=\"data row0 col0\" >12</td> \n",
       "        <td id=\"T_65edfd18_9b48_11e8_96aa_d49a20d1630frow0_col1\" class=\"data row0 col1\" >$4.23</td> \n",
       "        <td id=\"T_65edfd18_9b48_11e8_96aa_d49a20d1630frow0_col2\" class=\"data row0 col2\" >$50.76</td> \n",
       "    </tr>    <tr> \n",
       "        <th id=\"T_65edfd18_9b48_11e8_96aa_d49a20d1630flevel0_row1\" class=\"row_heading level0 row1\" >82</th> \n",
       "        <th id=\"T_65edfd18_9b48_11e8_96aa_d49a20d1630flevel1_row1\" class=\"row_heading level1 row1\" >Nirvana</th> \n",
       "        <td id=\"T_65edfd18_9b48_11e8_96aa_d49a20d1630frow1_col0\" class=\"data row1 col0\" >9</td> \n",
       "        <td id=\"T_65edfd18_9b48_11e8_96aa_d49a20d1630frow1_col1\" class=\"data row1 col1\" >$4.90</td> \n",
       "        <td id=\"T_65edfd18_9b48_11e8_96aa_d49a20d1630frow1_col2\" class=\"data row1 col2\" >$44.10</td> \n",
       "    </tr>    <tr> \n",
       "        <th id=\"T_65edfd18_9b48_11e8_96aa_d49a20d1630flevel0_row2\" class=\"row_heading level0 row2\" >145</th> \n",
       "        <th id=\"T_65edfd18_9b48_11e8_96aa_d49a20d1630flevel1_row2\" class=\"row_heading level1 row2\" >Fiery Glass Crusader</th> \n",
       "        <td id=\"T_65edfd18_9b48_11e8_96aa_d49a20d1630frow2_col0\" class=\"data row2 col0\" >9</td> \n",
       "        <td id=\"T_65edfd18_9b48_11e8_96aa_d49a20d1630frow2_col1\" class=\"data row2 col1\" >$4.58</td> \n",
       "        <td id=\"T_65edfd18_9b48_11e8_96aa_d49a20d1630frow2_col2\" class=\"data row2 col2\" >$41.22</td> \n",
       "    </tr>    <tr> \n",
       "        <th id=\"T_65edfd18_9b48_11e8_96aa_d49a20d1630flevel0_row3\" class=\"row_heading level0 row3\" >92</th> \n",
       "        <th id=\"T_65edfd18_9b48_11e8_96aa_d49a20d1630flevel1_row3\" class=\"row_heading level1 row3\" >Final Critic</th> \n",
       "        <td id=\"T_65edfd18_9b48_11e8_96aa_d49a20d1630frow3_col0\" class=\"data row3 col0\" >8</td> \n",
       "        <td id=\"T_65edfd18_9b48_11e8_96aa_d49a20d1630frow3_col1\" class=\"data row3 col1\" >$4.88</td> \n",
       "        <td id=\"T_65edfd18_9b48_11e8_96aa_d49a20d1630frow3_col2\" class=\"data row3 col2\" >$39.04</td> \n",
       "    </tr>    <tr> \n",
       "        <th id=\"T_65edfd18_9b48_11e8_96aa_d49a20d1630flevel0_row4\" class=\"row_heading level0 row4\" >103</th> \n",
       "        <th id=\"T_65edfd18_9b48_11e8_96aa_d49a20d1630flevel1_row4\" class=\"row_heading level1 row4\" >Singed Scalpel</th> \n",
       "        <td id=\"T_65edfd18_9b48_11e8_96aa_d49a20d1630frow4_col0\" class=\"data row4 col0\" >8</td> \n",
       "        <td id=\"T_65edfd18_9b48_11e8_96aa_d49a20d1630frow4_col1\" class=\"data row4 col1\" >$4.35</td> \n",
       "        <td id=\"T_65edfd18_9b48_11e8_96aa_d49a20d1630frow4_col2\" class=\"data row4 col2\" >$34.80</td> \n",
       "    </tr></tbody> \n",
       "</table> "
      ],
      "text/plain": [
       "<pandas.io.formats.style.Styler at 0x109df2278>"
      ]
     },
     "execution_count": 10,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# Take the most_popular items data frame and change the sorting to find highest total purchase value\n",
    "popular_formatted = most_popular_items.sort_values([\"Total Purchase Value\"],\n",
    "                                                   ascending=False).head()\n",
    "# Format with currency style\n",
    "popular_formatted.style.format({\"Item Price\":\"${:,.2f}\",\n",
    "                                \"Total Purchase Value\":\"${:,.2f}\"})"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": []
  }
 ],
 "metadata": {
  "anaconda-cloud": {},
  "kernel_info": {
   "name": "python3"
  },
  "kernelspec": {
   "display_name": "Python 3",
   "language": "python",
   "name": "python3"
  },
  "language_info": {
   "codemirror_mode": {
    "name": "ipython",
    "version": 3
   },
   "file_extension": ".py",
   "mimetype": "text/x-python",
   "name": "python",
   "nbconvert_exporter": "python",
   "pygments_lexer": "ipython3",
   "version": "3.6.5"
  },
  "nteract": {
   "version": "0.8.4"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 2
}
