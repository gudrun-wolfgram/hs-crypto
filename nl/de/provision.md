---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-21"

Keywords: provision, instance of Hyper Protect Crypto Services

subcollection: hs-crypto

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:important: .important}
{:gif: data-image-type='gif'}

# Den Service bereitstellen
{: #provision}

Sie können eine Instanz von {{site.data.keyword.cloud_notm}} {{site.data.keyword.hscrypto}} erstellen, indem Sie die {{site.data.keyword.cloud_notm}}-Konsole oder die {{site.data.keyword.cloud_notm}}-Befehlszeilenschnittstelle verwenden.
{: shortdesc}

## Bereitstellung über {{site.data.keyword.cloud_notm}}-Konsole durchführen
{: #provision-gui}

Zur Bereitstellung einer Instanz von {{site.data.keyword.hscrypto}} über die {{site.data.keyword.cloud_notm}}-Konsole führen Sie die folgenden Schritte aus:

1. [Melden Sie sich bei Ihrem {{site.data.keyword.cloud_notm}}-Konto ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://cloud.ibm.com/){: new_window} an.
2. Klicken Sie auf **Katalog**, um die Liste der Services anzuzeigen, die unter {{site.data.keyword.cloud_notm}} zur Verfügung stehen.
3. Klicken Sie im Navigationsbereich 'Alle Kategorien' auf die Kategorie **Sicherheit und Identität**.
4. Klicken Sie in der Serviceliste auf die **{{site.data.keyword.hscrypto}}**-Kachel.
5. **Optional**: Fügen Sie im Feld **Tags** Tags hinzu, um Ihre Ressourcen zu organisieren. Wenn es sich um abrechnungsbezogene Tags handelt, empfiehlt es sich möglicherweise, die Tags als Schlüssel/Wert-Paare zu schreiben, um zusammengehörige Tags zu gruppieren, z. B. `costctr:124`. Weitere Informationen zu Tags finden Sie unter [Mit Tags arbeiten](/docs/resources?topic=resources-tag#tag). 
6. Wählen Sie unter **Anzahl der Verschlüsselungseinheiten** die Anzahl der Verschlüsselungseinheiten aus, die Ihren Leistungsanforderungen entspricht. 

  Eine Serviceinstanz unterstützt bis zu sechs Verschlüsselungseinheiten. In einer Produktionsumgebung wird empfohlen, mindestens zwei Verschlüsselungseinheiten auszuwählen, um eine hohe Verfügbarkeit zu ermöglichen. Wenn Sie drei oder mehr Verschlüsselungseinheiten auswählen, werden diese Verschlüsselungseinheiten auf drei unterstützte Verfügbarkeitszonen in der ausgewählten Region verteilt.
  {: important}
7. Klicken Sie auf **Erstellen**, um eine Instanz von {{site.data.keyword.hscrypto}} im Konto, in der Region und in der Ressourcengruppe bereitzustellen, in dem/der Sie angemeldet sind. 

![Service bereitstellen](image/provisioning.gif "Service bereitstellen")
{: gif}

*Abbildung 1. Service bereitstellen*

<!-- ## Provisioning from the {{site.data.keyword.cloud_notm}} CLI
{: #provision-cli}

To provision an instance of {{site.data.keyword.hscrypto}} using the {{site.data.keyword.cloud_notm}} CLI, complete the following steps:

1. Download and install the [{{site.data.keyword.cloud_notm}} CLI](/docs/cli/index.html#overview){: new_window} with the following command:

    ```sh
    curl -sl https://ibm.biz/idt-installer | bash
    ```
    {: pre}

    **Notes:** For more information about the {{site.data.keyword.cloud_notm}} CLI, see [Getting started with the {{site.data.keyword.cloud_notm}} CLI](/docs/cli/index.html#overview){: new_window}.

2. Log in to {{site.data.keyword.cloud_notm}} through the {{site.data.keyword.cloud_notm}} CLI with the following command:

    ```sh
    ibmcloud login
    ```
    {: pre}

    **Notes:** If the login fails, run the `ibmcloud login --sso` command to try again. The `--sso` parameter is required when you log in with a federated ID. If this option is used, go to the link listed in the CLI output to generate a one-time passcode. -->

<!-- ### Creating a service instance within your account
{: #provision-acct-lvl}

To simplify access to your encryption keys with [{{site.data.keyword.iamlong}} roles](/docs/iam/users_roles.html#iamusermanrol), you can create one or more instances of the {{site.data.keyword.hscrypto}} service within an account, without needing to specify an org and space.

1. Log in to {{site.data.keyword.cloud_notm}} through the [{{site.data.keyword.cloud_notm}} CLI](/docs/cli/index.html#overview){: new_window}.

    ```sh
    ibmcloud login
    ```
    {: pre}
    **Notes:** If the login fails, run the `ibmcloud login --sso` command to try again. The `--sso` parameter is required when you log in with a federated ID. If this option is used, go to the link listed in the CLI output to generate a one-time passcode.

2. Select the account, region, and resource group where you would like to create a {{site.data.keyword.hscrypto}} service instance.

    You can use the following command to set your target region and resource group.

    ```sh
    ibmcloud target -r <region_name> -g <resource_group_name>
    ```
    {: pre}

3. Provision an instance of {{site.data.keyword.hscrypto}} within that account and resource group.

    ```sh
    ibmcloud resource service-instance-create <instance_name> kms tiered-pricing
    ```
    {: pre}

    Replace `<instance_name>` with a unique alias for your service instance.

4. Optional: Verify that the service instance was created successfully.

    ```sh
    ibmcloud resource service-instances
    ```
    {: pre}

### Creating a service instance within an org and space
{: #provision-space-lvl}

To manage access to your encryption keys with [Cloud Foundry roles](/docs/iam/cfaccess.html), you can create an instance of the {{site.data.keyword.hscrypto}} service within a specified organization and space.  

1. Log in to {{site.data.keyword.cloud_notm}} through the [{{site.data.keyword.cloud_notm}} CLI](/docs/cli/index.html#overview){: new_window}.

    ```sh
    ibmcloud login
    ```
    {: pre}
    **Note:** If the login fails, run the `ibmcloud login --sso` command to try again. The `--sso` parameter is required when you log in with a federated ID. If this option is used, go to the link listed in the CLI output to generate a one-time passcode.

2. Select the account, region, organization, and space where you would like to create a {{site.data.keyword.hscrypto}} service instance.

    You can use the following command to set your target region, org, and space.

    ```sh
    ibmcloud target -r <region> -o <organization_name> -s <space_name>
    ```
    {: pre}

3. Provision an instance of {{site.data.keyword.hscrypto}} within that account, region, organization, and space.

    ```sh
    ibmcloud service create kms tiered-pricing <instance_name>
    ```
    {: pre}

    Replace `<instance_name>` with a unique alias for your service instance.

4. Optional: Verify that the service instance was created successfully.

    ```sh
    ibmcloud service list
    ```
    {: pre}
-->

### Weitere Schritte
{: #provision-next}

Weitere Informationen zur programmgesteuerten Verwaltung von Schlüsseln [finden Sie in der{{site.data.keyword.hscrypto}}-API-Referenz ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/apidocs/hs-crypto){: new_window}. 
