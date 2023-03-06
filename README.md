# Resume Rater
![](assets/Resume_image.jpg)

#### Sample of good extraction (high precision; with rating)
`src/data/test/Dong Xing_Catherine Zhang_Equity Research Intern.pdf`

    Name: ZHANG Xiaoyu Catherine
    Email: zhangxy923@126.com
    Number: +852 54871558
    City/Country: China

    Work Experience:
    6 years 4 months
    - Dongxing Securities Shenzhen, China
    - Equity Research Intern, Computer Team Jan 2017 - Now
    - AI and Internet+. Collect and analyze industry and firms’ information; get financial data by Wind and Bloomberg).
    - Roland Berger Strategy Consultants Shanghai, China
    - Part-time Assistant, Financial Services Department Sep 2016 - Nov 2016
    - Bank of China Beijing, China
    - Clients Manager, Individual Financial Department Sep 2012 - Jun 2016
    - PROJECT EXPERIENCE
    - ABT) Hong Kong
    - Team Leader Mar 2017 - Apr 2017

    Education:
    5 years 1 months
    - City University of Hong Kong Hong Kong
    - Master of Science in Financial Services Aug 2016 - Nov 2017
    - Investment, Derivatives and Risk Management, Corporate Finance, Financial Statement Analysis,
    - Fixed Income Securities, Credit Risk Management.
    - Capital University of Economics and Business Beijing, China
    - Bachelor of Science in Finance Sep 2008 - Jun 2012
    - RenMin Scholarship, 7 times (Top 10%).
    - Investment Banking, Securities Investment Fund, Financial Model Design, Accounting, Economic Law.
    - The University of Hong Kong Hong Kong
    - Exchange Student Jul 2011- Aug 2011
    - Financial Analysis, Marketing Management, Writing.

    Skills:
    Security, Finance, Writing, Analysis, Accounting, Research, Marketing, Email, Economics,
    Strategy, Excel, Powerpoint, Financial analysis, Presentation, Design, Technical,
    Cfa, Banking, Reports, Due diligence, Word, Mobile, Risk management, Analyze,
    Ai, Data analysis, Microsoft office, Modeling
    ----------
    Rating: 9

#### Sample of not-so-good extraction (low precision; with rating)
`src/data/test/Brawn Capital_Minori Yoshida_FM.docx`

    Name: Minori Yoshida Yan Wo Yuet Building
    Email: y.minori512@gmail.com
    Number: +852-9544-5637
    City/Country: Hong Kong

    Work Experience:
    6 years 4 months
    - Brawn Capital Limited, Central, Hong Kong
    - August 2016 Present
    - Finance Manager
    - Manage financials of project finance working closely with developer and asset management company in Japan
    - Establish and improve internal financial processes of both project and corporate
    - Manage budget, financial reports and tax flings both in Hong Kong and Japan
    - KPMG AZSA LLC, Tokyo, Japan February 2012 February 2015
    - Audit Practice
    - Perform annual financial audits, quarterly reviews under J-GAAP and internal control audit under J-SOX for audit engagements of various clients including one of the biggest Japanese public companies listed in Tokyo Stock Exchange
    - Perform reporting package reviews under IFRS and US-GAAP for various clients who have overseas parent companies
    - Consult on management accounting issues and deliver solutions.
    - Identify and communicate accounting and auditing matters to managers and partners

    Education:
    3 years 11 months
    - Meiji University Bachelor of Business Administration April 2007 March 2011
    - Department of Accounting

    Skills:
    Sales, Budget, Analysis, Auditing, Process, Tax, Administration, Reports, Gaap, Budgeting,
    Financial analysis, English, Reporting, Finance, Modeling, Accounting, Financial reports,
    Consulting, Journal entries, Flower, Communication, Audit, Word, Relationship management,
    Excel
    ----------
    Rating: 8


## Installation

Use Python3

    pip3 install virtualenv 
    [use pip instead of pip3 if it doesn't work]
    
    python -m venv env
    [create a virtual environment for dependencies. dont skip this]

    .\env\Scripts\activate [Windows]
    source env/bin/activate [MacOS]
    if it doesn't work, follow this [guide](https://packaging.python.org/en/latest/guides/installing-using-pip-and-virtual-environments/)

    pip3 install -r requirements.txt 
    [use pip instead of pip3 if it doesn't work]
    
    python3 pre_requisites.py 
    [use python instead of python3 if it doesn't work]

Test run

    python3 main.py --type fixed "src/data/test/Agnes-Kim.pdf" --model_name model 
    [use python instead of python3 if it doesn't work]


## Usage
### For testing:
Test resumes can be found in `src/data/test`

#### Supervised (Fixed Keywords)
For the fixed keyword implementation, the pre-trained model is trained on the keywords:

`[fund, asset, investment, accounting, trust, strategy]`

To use it, type:

      python3 main.py path/to/resume

or, long-form,

      python3 main.py --type fixed path/to/resume


for specific model (no default):

      python3 main.py --type fixed path/to/resume --model_name model


or using model path (no default):

      python3 main.py --type fixed path/to/resume --model_path path/to/model


Resume should be `pdf` or `docx` format
Pre-trained model: `src/models/model_fixed/model.json`
Pre-trained model_name: `model`

#### Unsupervised (LDA-generated keywords)
To use the LDA-generated keyword implementation:

      python3 main.py --type lda path/to/resume

for specific model:

      python3 main.py --type lda path/to/resume --model_name model

or using model path (no default):

      python3 main.py --type lda path/to/resume --model_path path/to/model

Resume should be `pdf` or `docx` format
Pre-trained model: `src/models/model_lda/model.json`
Pre-trained model name: `model`

---
### For training:
Training resumes can be found in `src/data/train` (size=1468) [seems like the author removed these files]

or for a smaller dataset (size=30), `src/data/sample_train` [seems like the author removed these files]
#### Supervised (Fixed Keywords)
For the fixed keyword implementation:

      python3 main.py --train path/of/training_directory --type fixed --keywords fund asset investment accounting trust strategy --model_name abc_model

Model and keywords will be saved in `src/models/model_fixed`

#### Unsupervised (LDA-generated keywords)
For the LDA-generated keyword implementation:

      python3 main.py --train path/of/training_directory --type lda  --model_name abc_model

Model and LDA model will be saved in `src/models/model_lda`