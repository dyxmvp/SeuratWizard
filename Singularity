Bootstrap: shub
From: dyxmvp/SeuratWizard

%labels
  Maintainer dyx

%environment
  source /opt/rh/devtoolset-7/enable
  export SHINY_PORT=31337

%help
  This will run a simple shiny app from the gallery example at
  https://github.com/dyxmvp/SeuratWizard

%runscript
  cd /inst/shiny
  exec R -e "options(browser='firefox');shiny::runApp(host='0.0.0.0', port=$SHINY_PORT, launch.browser=TRUE)"

%post
  source /opt/rh/devtoolset-7/enable
  yum update -y
  yum install -y firefox wget
  wget https://github.com/dyxmvp/SeuratWizard/archive/master.zip
  unzip master.zip
  cd /inst/shiny
  Rscript -e "install.packages('packrat', repos='http://cran.rstudio.com')"
  Rscript -e "packrat::init();install.packages('shiny', repos='http://cran.rstudio.com')"
  yum clean all && rm -rf /var/cache/yum
