#mcr.microsoft.com/aiforearth/base-py:version
ARG  BASE_IMAGE=nvidia/cuda:9.2-runtime-ubuntu16.04
FROM $BASE_IMAGE

COPY ./base-py/requirements /ai4e_api_tools/requirements
COPY ./base-py/ai4e_api_tools /ai4e_api_tools/
COPY ./common/sas_blob.py /ai4e_api_tools/

ENV PATH /usr/local/envs/ai4e_py_api/bin:$PATH
ENV PYTHONPATH="${PYTHONPATH}:/ai4e_api_tools"

# Install Miniconda, Flask, Supervisor, uwsgi
RUN ./ai4e_api_tools/requirements/install-api-hosting-reqs.sh

# Install Azure Blob SDK
RUN ./ai4e_api_tools/requirements/install-azure-blob.sh

# Install Opencensus
RUN ./ai4e_api_tools/requirements/install-opencensus.sh

# Install Application Insights
RUN ./ai4e_api_tools/requirements/install-appinsights.sh

# Expose opencensus ports
EXPOSE 55678
EXPOSE 50001