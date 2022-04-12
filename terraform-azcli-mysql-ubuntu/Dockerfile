FROM ubuntu:focal

RUN apt update &&\
    apt install --no-install-recommends curl lsb-release mysql-client gnupg software-properties-common ca-certificates apt-transport-https coreutils gnupg -y &&\
    curl -sL https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor | tee /etc/apt/trusted.gpg.d/microsoft.gpg > /dev/null &&\
    AZ_REPO=$(lsb_release -cs) && echo "deb [arch=amd64] https://packages.microsoft.com/repos/azure-cli/ $AZ_REPO main" | tee /etc/apt/sources.list.d/azure-cli.list &&\
    apt update && apt install azure-cli -y &&\
    curl -sL https://aka.ms/InstallAzureCLIDeb | bash &&\
    curl -fsSL https://apt.releases.hashicorp.com/gpg | apt-key add - &&\
    apt-add-repository "deb [arch=amd64] https://apt.releases.hashicorp.com $(lsb_release -cs) main" &&\
    apt update && apt install terraform -y &&\
    apt clean && apt remove -y lsb-release gnupg software-properties-common ca-certificates apt-transport-https curl && apt autoremove -y && rm -rf /var/lib/apt/lists/*;