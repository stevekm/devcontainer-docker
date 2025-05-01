FROM mcr.microsoft.com/devcontainers/base:ubuntu-24.04

# Install AWS CLI
RUN apt-get update && apt-get install -y unzip curl bzip2 iputils-ping \
    && curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip" \
    && unzip awscliv2.zip && ./aws/install && rm -f "awscliv2.zip"

# Install Singularity
RUN apt-get install -y singularity-container=4.1.1+ds2-1ubuntu0.2

# Install Docker
# https://docs.docker.com/engine/install/ubuntu/
# Add Docker's official GPG key:
RUN apt-get install ca-certificates curl && \
install -m 0755 -d /etc/apt/keyrings && \
curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc && \
chmod a+r /etc/apt/keyrings/docker.asc && \
echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | tee /etc/apt/sources.list.d/docker.list > /dev/null
RUN apt-get update && \
    apt-get install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

# Add default user to Docker group for non-root access
RUN getent group docker || groupadd docker
RUN usermod -aG docker vscode

# Clean up apt
RUN apt-get clean && rm -rf /var/lib/apt/lists/*

# Install conda ; based on https://github.com/conda-forge/docker-images/blob/fe1a5326926fd75bb90bfa7bfe9e39e6509ab9f1/miniforge3/Dockerfile
ENV CONDA_DIR=/opt/conda
ENV PATH=${CONDA_DIR}/bin:${PATH}
RUN curl -fsSLo Miniforge3.sh "https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge3-$(uname)-$(uname -m).sh" && \
bash Miniforge3.sh -b -p "${CONDA_DIR}" && \
rm -f Miniforge3.sh
RUN conda init --system bash zsh
# https://www.linfo.org/etc_skel.html
#RUN echo ". ${CONDA_DIR}/etc/profile.d/conda.sh && conda activate base" >> /etc/skel/.bashrc
#RUN echo ". ${CONDA_DIR}/etc/profile.d/conda.sh && conda activate base" >> ~/.bashrc

# install Ansible
RUN conda install -y -n base conda-forge::ansible=11.0.0



