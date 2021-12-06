
<!-- README.md is generated from README.Rmd. Please edit that file -->

# IDEA <a href='https://github.biogen.com/pages/biometrics/SEER/'><img src="man/figures/app_ICON.png" align="right" height="139"/></a>

IDEA is a shiny app to easily create custom tables and figures from
ADaM-ish datasets.

## Purpose

One of `IDEA`‘s goals is to develop clinical tables that abide to
Biogen’s table standards leveraged for submission filings, officially
called
“[STAN](https://biib.sharepoint.com/:w:/r/sites/ADSTCS/DS&G/_layouts/15/Doc.aspx?sourcedoc=%7B86cf7567-db46-4983-9a12-fdc63e77cf98%7D&action=view&wdAccPdf=0&wdparaid=688A3ED1&CID=B3A09B8B-6A35-4F43-A484-5E9EF88CD5FA&wdLOR=c8053EEAB-66ED-4CA0-9B71-331B73267CD8)”
(short for ’standard analysis’). However, this is only secondary to the
app’s primary purpose: providing rich exploratory capabilities for
clinical studies. High-level features of the app allows users to produce
customized tables using a point-and-click interface, examine trends in a
patient populations with dynamic figures, and supply visualizations that
narrow in on single patient profile. The beauty of this application is
that the user doesn’t have to write a lick of code to acquire abundant
insights on your study data, so it aims to serve a large population of
clinical personnel.

## Scope

As previously mentioned, IDEA can only accept datasets that conform to
CDISC ADaM standards with some minor flexibility (see upload
requirements for more details \[insert link here\]. At this time, the
app only accepts sas7bdat files.

If you’re looking to regularly generate R code for tables, the IDEA app
has a built-in export feature that downloads an R script that reproduces
any analysis performed in the app. However, if you already have
experience with R programming, we’d highly recommend learning Biogen’s
(internal)
[`stanly`](https://github.biogen.com/pages/biometrics/stanly/) package
to expand on the R code that IDEA yields for STAN-complaint tables. To
summarize, the `stanly` package is a suite of functions designed for
Biogen SAS programmers capable of producing 50+ STAN outputs.

## Usage

IDEA is primarily an application, so no installation is necessary.
Simply access Biogen’s network and start using the app: [IDEA
application](https://awshpc22133.abc.amazon.biogen.com/IDEA/) However,
if you choose to export R code from the Table Generatory, you will need
a the `IDEA` package installed on your machine locally. See installation
instructions in the next section below.

Please review the “[Getting
Started](https://github.biogen.com/pages/biometrics/IDEA/articles/IDEA.html)”
guide to to learn how to answer all your analysis questions with `IDEA`
. If the application can’t solve your question, we want to know about
it! Submit all feature requests to `adshelp@digicomm.jira.com` and
mention `IDEA`.

Below are visuals of IDEA’S primary features/ tabs mentioned above.

### Table Generator

\[insert gif\]

### Population Explorer

\[insert gif\]

### Individual Explorer

\[insert gif\]

## Install IDEA R package

If you’d like to run code generated by `IDEA` or if you are an R
developer looking to contribute to the package, welcome! We’ve provided
a slurry of information for on-boarding with IDEA.

The good news is that you don’t need GitHub access in order to install
IDEA. You just need to be an HPC user to access Biogen’s internal
[Rstudio Package
Manager](http://10.240.22.159:4242/client/#/repos/5/packages/IDEA)
(RSPM) where the package is hosted. If you cannot access RSPM from the
above link, then you’ll need to submit a simple BAM request as detailed
below. If you can access the RSPM link, you can skip the access request
step below.

#### Request Access for HPC account

Click this [service-now
link](https://biogen.service-now.com/it?id=sc_cat_item&sys_id=e9b6a50edb026380846573198c96197f)
OR go to Synapse &gt; IT Help &gt; Infrastructure & Operation &gt; HPC
(High Performance Computing). When redirected to the request form,
select “Access Request” for the `HPC Request Type`, then “HPC Account”
for the `Access request` field that appears.

In the description field, type: “Please create an account for me on the
Cambridge Research cluster (CAMHPC).” Also include the name of your
department (CompChem, CompBio, SciComp, Proteomics, etc.). You will
receive an email when your account is provisioned, typically within one
business day.

#### Install IDEA from RSPM

Once you have confirmed access to RSPM, then execute the following code
to install the package to your local machine:

``` r
# For HPC users, add RSPM's GHE repo:
options(repos = c(
  CRAN = "https://cran.rstudio.com/",
  ghe = "http://10.240.22.159:4242/Git-Biogen/latest")
)
options('repos') # to confirm "ghe" was added
install.packages("IDEA")
```

Now you can access all the exported function from `IDEA` that help users
reproduce analysis performed in the app. Using the dev/run\_dev.R file,
you can even run the application locally:

``` r
# Set options here
options(golem.app.prod = FALSE) # TRUE = production mode, FALSE = development mode

# Detach all loaded packages and clean your environment
golem::detach_all_attached()

# Document and reload your package, which runs these three functions...
golem::document_and_reload()

# Run the application 
run_app()
```
