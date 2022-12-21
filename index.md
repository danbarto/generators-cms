---
layout: workshop      # DON'T CHANGE THIS.
# More detailed instructions (including how to fill these variables for an
# online workshop) are available at
# https://carpentries.github.io/workshop-template/customization/index.html
venue: "LPC at Fermilab"        # brief name of the institution that hosts the workshop without address (e.g., "Euphoric State University")
address: "Batavia IL 60510"      # full street address of workshop (e.g., "Room A, 123 Forth Street, Blimingen, Euphoria"), videoconferencing URL, or 'online'
country: "United States"      # lowercase two-letter ISO country code such as "fr" (see https://en.wikipedia.org/wiki/ISO_3166-1#Current_codes) for the institution that hosts the workshop
language: "en"     # lowercase two-letter ISO language code such as "fr" (see https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes) for the workshop
latitude: "41.842258"        # decimal latitude of workshop venue (use https://www.latlong.net/)
longitude: "-88.245781"       # decimal longitude of the workshop venue (use https://www.latlong.net)
humandate: "Jan 9-13, 2022"    # human-readable dates for the workshop (e.g., "Feb 17-18, 2020")
humantime: "9:00 am - 5:00 pm"    # human-readable times for the workshop e.g., "9:00 am - 4:30 pm CEST (7:00 am - 2:30 pm UTC)"
startdate: 2022-01-09      # machine-readable start date for the workshop in YYYY-MM-DD format like 2015-01-01
enddate: 2022-01-13        # machine-readable end date for the workshop in YYYY-MM-DD format like 2015-01-02
instructor: ["Daniel Spitzbart", "Nadja Strobbe"] # boxed, comma-separated list of instructors' names as strings, like ["Kay McNulty", "Betty Jennings", "Betty Snyder"]
helper: ["Christian Herwig", "Michael Krohn", "Steve Mrenne"]     # boxed, comma-separated list of helpers' names, like ["Marlyn Wescoff", "Fran Bilas", "Ruth Lichterman"]
email: ["daniel.spitzbart@cern.ch"]    # boxed, comma-separated list of contact email addresses for the host, lead instructor, or whoever else is handling questions, like ["marlyn.wescoff@example.org", "fran.bilas@example.org", "ruth.lichterman@example.org"]
collaborative_notes:  # optional: URL for the workshop collaborative notes, e.g. an Etherpad or Google Docs document (e.g., https://pad.carpentries.org/2015-01-01-euphoria)
eventbrite:           # optional: alphanumeric key for Eventbrite registration, e.g., "1234567890AB" (if Eventbrite is being used)
---

{% comment %} See instructions in the comments below for how to edit specific sections of this workshop template. {% endcomment %}

{% comment %}
HEADER

Edit the values in the block above to be appropriate for your workshop.
If the value is not 'true', 'false', 'null', or a number, please use
double quotation marks around the value, unless specified otherwise.
And run 'make workshop-check' *before* committing to make sure that changes are good.
{% endcomment %}


{% comment %}
Check DC curriculum
{% endcomment %}

{% if site.carpentry == "dc" %}
{% unless site.curriculum == "dc-astronomy" or site.curriculum == "dc-ecology" or site.curriculum == "dc-genomics" or site.curriculum == "dc-socsci" or site.curriculum == "dc-geospatial" %}
<div class="alert alert-warning">
It looks like you are setting up a website for a Data Carpentry curriculum but you haven't specified the curriculum type in the <code>_config.yml</code> file (current value in <code>_config.yml</code>: "<strong>{{ site.curriculum }}</strong>", possible values: <code>dc-astronomy</code>, <code>dc-ecology</code>, <code>dc-genomics</code>, <code>dc-socsci</code>, or <code>dc-geospatial</code>). After editing this file, you need to run <code>make serve</code> again to see the changes reflected.
</div>
{% endunless %}
{% endif %}

{% comment %}
Check SWC curriculum
{% endcomment %}

{% if site.carpentry == "swc" %}
{% unless site.curriculum == "swc-inflammation" or site.curriculum == "swc-gapminder" %}
<div class="alert alert-warning">
It looks like you are setting up a website for a Software Carpentry curriculum but you haven't specified the curriculum type in the <code>_config.yml</code> file (current value in <code>_config.yml</code>: "<strong>{{ site.curriculum }}</strong>", possible values: <code>swc-inflammation</code>, or <code>swc-gapminder</code>). After editing this file, you need to run <code>make serve</code> again to see the changes reflected.
</div>
{% endunless %}
{% endif %}

{% comment %}
EVENTBRITE

This block includes the Eventbrite registration widget if
'eventbrite' has been set in the header.  You can delete it if you
are not using Eventbrite, or leave it in, since it will not be
displayed if the 'eventbrite' field in the header is not set.
{% endcomment %}
{% if page.eventbrite %}
<strong>Some adblockers block the registration window. If you do not see the
  registration box below, please check your adblocker settings.</strong>
<iframe
  src="https://www.eventbrite.com/tickets-external?eid={{page.eventbrite}}&ref=etckt"
  frameborder="0"
  width="100%"
  height="280px"
  scrolling="auto">
</iframe>
{% endif %}


<h2 id="general">General Information</h2>

{% comment %}
INTRODUCTION

Edit the general explanatory paragraph below if you want to change
the pitch.
{% endcomment %}
{% if site.carpentry == "swc" %}
{% include swc/intro.html %}
{% elsif site.carpentry == "dc" %}
{% include dc/intro.html %}
{% elsif site.carpentry == "lc" %}
{% include lc/intro.html %}
{% endif %}

{% if site.pilot %}
This is a pilot workshop, testing out a lesson that is still under development. The lesson authors would appreciate any feedback you can give them about the lesson content and suggestions for how it could be further improved.
{% endif %}

{% comment %}
AUDIENCE

Explain who your audience is.  (In particular, tell readers if the
workshop is only open to people from a particular institution.
{% endcomment %}
{% if site.carpentry == "swc" %}
{% include swc/who.html %}
{% elsif site.carpentry == "dc" %}
{% include dc/who.html %}
{% elsif site.carpentry == "lc" %}
{% include lc/who.html %}
{% endif %}

{% comment %}
LOCATION

This block displays the address and links to maps showing directions
if the latitude and longitude of the workshop have been set.  You
can use https://www.latlong.net/ to find the lat/long of an
address.
{% endcomment %}
{% assign begin_address = page.address | slice: 0, 4 | downcase  %}
{% if page.address == "online" %}
{% assign online = "true_private" %}
{% elsif begin_address contains "http" %}
{% assign online = "true_public" %}
{% else %}
{% assign online = "false" %}
{% endif %}
{% if page.latitude and page.longitude and online == "false" %}
<p id="where">
  <strong>Where:</strong>
  {{page.address}}.
  Get directions with
  <a href="//www.openstreetmap.org/?mlat={{page.latitude}}&mlon={{page.longitude}}&zoom=16">OpenStreetMap</a>
  or
  <a href="//maps.google.com/maps?q={{page.latitude}},{{page.longitude}}">Google Maps</a>.
</p>
{% elsif online == "true_public" %}
<p id="where">
  <strong>Where:</strong>
  online at <a href="{{page.address}}">{{page.address}}</a>.
  If you need a password or other information to access the training,
  the instructor will pass it on to you before the workshop.
</p>
{% elsif online == "true_private" %}
<p id="where">
  <strong>Where:</strong> This training will take place online.
  The instructors will provide you with the information you will need to connect to this meeting.
</p>
{% endif %}

{% comment %}
DATE

This block displays the date and links to Google Calendar.
{% endcomment %}
{% if page.humandate %}
<p id="when">
  <strong>When:</strong>
  {{page.humandate}}.
  {% include workshop_calendar.html %}
</p>
{% endif %}

{% comment %}
SPECIAL REQUIREMENTS

Modify the block below if there are any special requirements.
{% endcomment %}
<p id="requirements">
  <strong>Requirements:</strong>
  {% if online == "false" %}
    Participants must bring a laptop with a
    Mac, Linux, or Windows operating system (not a tablet, Chromebook, etc.) that they have administrative privileges on.
  {% else %}
    Participants must have access to a computer with a
    Mac, Linux, or Windows operating system (not a tablet, Chromebook, etc.) that they have administrative privileges on.
  {% endif %}
  They should have a few specific software packages installed (listed <a href="#setup">below</a>).
</p>

{% comment %}
ACCESSIBILITY

Modify the block below if there are any barriers to accessibility or
special instructions.
{% endcomment %}
<p id="accessibility">
  <strong>Accessibility:</strong>
{% if online == "false" %}
  We are committed to making this workshop
  accessible to everybody.  For workshops at a physical location, the workshop organizers have checked that:
</p>
<ul>
  <li>The room is wheelchair / scooter accessible.</li>
  <li>Accessible restrooms are available.</li>
</ul>
<p>
  Materials will be provided in advance of the workshop and
  large-print handouts are available if needed by notifying the
  organizers in advance.  If we can help making learning easier for
  you (e.g. sign-language interpreters, lactation facilities) please
  get in touch (using contact details below) and we will
  attempt to provide them.
</p>
{% else %}
  We are dedicated to providing a positive and accessible learning environment for all. Please
  notify the instructors in advance of the workshop if you require any accommodations or if there is
  anything we can do to make this workshop more accessible to you.
</p>
{% endif %}

{% comment %}
CONTACT EMAIL ADDRESS

Display the contact email address set in the configuration file.
{% endcomment %}
<p id="contact">
  <strong>Contact:</strong>
  Please email
  {% if page.email %}
  {% for email in page.email %}
  {% if forloop.last and page.email.size > 1 %}
  or
  {% else %}
  {% unless forloop.first %}
  ,
  {% endunless %}
  {% endif %}
  <a href='mailto:{{email}}'>{{email}}</a>
  {% endfor %}
  {% else %}
  to-be-announced
  {% endif %}
  for more information.
</p>

<p id="roles">
  <strong>Roles:</strong>
  To learn more about the roles at the workshop (who will be doing what),
  refer to <a href="https://carpentries.org/workshop_faq/#what-are-the-roles-of-everyone-participating-in-a-workshop">our Workshop FAQ</a>.
</p>

{% comment %}
WHO CAN ATTEND?

If you would like to specify who can attend the workshop,
you can use the section below.

Move the 'endcomment' tag above the beginning of the following
<p> tag to make this section visible.

Edit the text to match who can attend the workshop. For instance:
- This workshop is open to affiliates to ABC university.
- This workshop is open to the public.
- If you are interested in attending this workshop, contact me@example.com
  for more information

<p id="who-can-attend">
    <strong>Who can attend?:</strong>
    This workshop is open to ....
</p>
{% endcomment %}

<hr/>

{% comment%}
CODE OF CONDUCT
{% endcomment %}
<h2 id="code-of-conduct">Code of Conduct</h2>

<p>
Everyone who participates in Carpentries activities is required to conform to the <a href="https://docs.carpentries.org/topic_folders/policies/code-of-conduct.html">Code of Conduct</a>. This document also outlines how to report an incident if needed.
</p>

<p class="text-center">
  <a href="https://goo.gl/forms/KoUfO53Za3apOuOK2">
    <button type="button" class="btn btn-info">Report a Code of Conduct Incident</button>
  </a>
</p>
<hr/>


{% comment %}
Collaborative Notes

If you want to use an Etherpad, go to

https://pad.carpentries.org/YYYY-MM-DD-site

where 'YYYY-MM-DD-site' is the identifier for your workshop,
e.g., '2015-06-10-esu'.

Note we also have a CodiMD (the open-source version of HackMD)
available at https://codimd.carpentries.org
{% endcomment %}
{% if page.collaborative_notes %}
<h2 id="collaborative_notes">Collaborative Notes</h2>

<p>
We will use this <a href="{{ page.collaborative_notes }}">collaborative document</a> for chatting, taking notes, and sharing URLs and bits of code.
</p>
<hr/>
{% endif %}


# Setup

The following commands are tested on the LPC cluster, using the bash shell.
You can run `echo "$SHELL"` to check that you are indeed running bash.
Add the following lines to your `~/.bash_profile` file
~~~bash
export CDGPATH=${HOME}/nobackup/cmsdas_2023_gen
source /cvmfs/cms.cern.ch/cmsset_default.sh
~~~
{: .source}
Run `bash -l` to restart bash, or alternatively `source ~/.bash_profile` to activate your change. You don't need to rerun this command next time you re-login to the LPC cluster.

We start with pulling and installing the required CMS software (CMSSW).
We use two versions: the older 10.6.19 is used for sample generation,
while we will make use of the more up-to-date tools installed in 12.4.7 when we analyze the samples.
~~~bash
mkdir -p ${CDGPATH}

cd ${CDGPATH}
cmsrel CMSSW_10_6_19
cmsrel CMSSW_12_4_7
~~~
{: .source}

Downloading MadGraph5 v2.6.5 from a CMS mirror, which is the MG version that is currently used in CMS for Run 2 Ultra Legacy and Run 3 samples.
~~~bash
wget https://cms-project-generators.web.cern.ch/cms-project-generators/MG5_aMC_v2.6.5.tar.gz
tar xf MG5_aMC_v2.6.5.tar.gz
rm MG5_aMC_v2.6.5.tar.gz
~~~
{: .source}

Cloning the CMS generator repository:
~~~bash
git clone -b mg265UL https://github.com/cms-sw/genproductions.git genproductions_mg265
~~~
{: .source}

You can check that the MadGraph steering cards of the example we will be using are actually there:
~~~bash
ls -rtl genproductions/bin/MadGraph5_aMCatNLO/cards/examples/wplustest_4f_LO/
~~~
{: .source}

~~~
total 20
-rw-r--r-- 1 dspitzba us_cms   223 Dec 21 08:10 wplustest_4f_LO_proc_card.dat
-rw-r--r-- 1 dspitzba us_cms 15996 Dec 21 08:10 wplustest_4f_LO_run_card.dat
~~~
{: .output}

# Using MadGraph

## Standalone

## The CMS gridpack workflow

Instructions for gridpack generation go here

> ## Producing a gridpack
>
> Pull the image python:3.7-slim for Python 3.7 and then list all `python` images along with the `sl:7` image
>
> > ## Solution
> >
> > ~~~bash
> > docker pull python:3.7-slim
> > docker images --filter=reference="sl" --filter=reference="python"
> > ~~~
> > {: .source}
> >
> > ~~~
> > 
> > ~~~
> > {: .output}
> {: .solution}
{: .challenge}

## Inspecting the LHE file

--> show how to do this in standalone

# Parton Shower and Sample generation


## Showering LHE event

Use the lhe file to shower using a cmsDriver cfg

## Determining qcut

Keep this exercise?

## Creating NanoGEN

In the following steps we will use a pre-made gridpack: `/eos/uscms/store/user/cmsdas/2023/short_exercises/Generators/WJetsToLNu_HT-0toInf_slc7_amd64_gcc700_CMSSW_10_6_19_tarball.tar.xz`

Copy fragment from repo.

~~~bash
cd ${CDGPATH}/CMSSW_10_6_19/src
cmsenv
mkdir -p Configuration/GenProduction/python/
cp ${CDGPATH}/gen-cmsdas-2022/fragments/Hadronizer_TuneCP5_13TeV_MLM_5f_max2j_qCut10_LHE_pythia8_cff.py Configuration/GenProduction/python/
scram b -j 8
~~~
{: .source}

What is the qcut we are using here?

Run cmsDriver to create a cmsRun configuration file:
~~~bash
cmsDriver.py Configuration/GenProduction/python/Hadronizer_TuneCP5_13TeV_MLM_5f_max2j_qCut10_LHE_pythia8_cff.py --python_filename nanoGEN_cfg.py --eventcontent NANOAODGEN --customise Configuration/DataProcessing/Utils.addMonitoring --datatier NANOAOD --fileout file:NanoGEN.root --conditions auto:mc --beamspot Realistic25ns13TeVEarly2018Collision --step LHE,GEN,NANOGEN --geometry DB:Extended --era Run2_2018 --no_exec --mc -n 1000
~~~
{: .source}

Run cmsRun
~~~bash
cmsRun nanoGEN_cfg.py
~~~
{: .source}

Produces a flat ntuple ready for simple data analysis, following the same structure as a full-fledged NanoAOD with just generator information.

Provide a larger sample for later plots?


# Analysis

## Generator level distributions from NanoGEN

Calculate transverse mass from GenDressedLepton and GenMET
~~~bash
cd ${CDGPATH}/CMSSW_12_4_7/src; cmsenv; cd ${CDGPATH}/gen-cmsdas-2022
python analysis/plot_mt.py
~~~
{: .source}

## Systematic Uncertainties related to generators


# CMS Tools

McM, x-sec DB, DAS, GRASP

