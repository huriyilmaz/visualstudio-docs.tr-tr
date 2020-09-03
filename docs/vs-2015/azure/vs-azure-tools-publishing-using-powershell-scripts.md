---
title: Geliştirme ve test ortamlarında yayımlamak için Windows PowerShell betikleri kullanma | Microsoft Docs
description: Geliştirme ve test ortamlarında yayımlamak üzere Visual Studio 'da Windows PowerShell betiklerini nasıl kullanacağınızı öğrenin.
author: ghogen
manager: jillfra
assetId: 5fff1301-5469-4d97-be88-c85c30f837c1
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2016
ms.author: ghogen
ms.openlocfilehash: 6913ec4c80b5cb87cf6cd980ff2da73fab309a02
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "84184022"
---
# <a name="using-windows-powershell-scripts-to-publish-to-dev-and-test-environments"></a>Windows PowerShell betiklerini kullanarak geliştirme ve test ortamlarına yayımlama

Visual Studio 'da bir Web uygulaması oluşturduğunuzda, daha sonra Web sitenizin Azure App Service veya bir sanal makinede bir Web uygulaması olarak Azure 'a yayımlanmasını otomatikleştirmek için kullanabileceğiniz bir Windows PowerShell betiği oluşturabilirsiniz. Gereksinimlerinize uyacak şekilde Visual Studio düzenleyicisinde Windows PowerShell betiğini düzenleyebilir ve genişletebilirsiniz veya betiği var olan derleme, test ve yayımlama betiklerine entegre edebilirsiniz.

Bu betikleri kullanarak, geçici kullanım için sitenizin özelleştirilmiş sürümlerini (geliştirme ve test ortamları olarak da bilinir) sağlayabilirsiniz. Örneğin, bir Azure sanal makinesinde veya bir Web sitesindeki hazırlama yuvasında bir test paketini çalıştırmak, bir hatayı yeniden oluşturmak, bir hata düzeltmesini test etmek, önerilen bir değişikliği denemek veya bir demo ya da sunum için özel bir ortam ayarlamak üzere Web sitenizin belirli bir sürümünü kurabilirsiniz. Projenizi yayımlayan bir betik oluşturduktan sonra, komut dosyasını gerektiği gibi yeniden çalıştırarak özdeş ortamları yeniden oluşturabilir veya test için özel bir ortam oluşturmak üzere betiği kendi Web uygulamanızın derlemesi ile çalıştırabilirsiniz.

## <a name="prerequisites"></a>Önkoşullar

* Azure SDK 2,3 veya sonraki bir sürümü. Bkz. [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/downloads/). (Web projelerine yönelik betikleri oluşturmak için Azure SDK 'ya ihtiyacınız yoktur. Bu özellik, bulut hizmetlerinde Web rolleri değil Web projelerine yöneliktir.)
* Azure PowerShell 0.7.4 veya üzeri. Bkz. [Azure PowerShell'i yükleme ve yapılandırma](/powershell/azure/overview).
* [Windows PowerShell 3,0](/aspnet/aspnet/overview/developing-apps-with-windows-azure/building-real-world-cloud-apps-with-windows-azure/source-control) veya üzeri.

## <a name="additional-tools"></a>Ek araçlar

Azure geliştirme için Visual Studio 'da PowerShell ile çalışmaya yönelik ek araçlar ve kaynaklar mevcuttur. Bkz. [PowerShell Tools for Visual Studio](https://visualstudiogallery.msdn.microsoft.com/c9eb3ba8-0c59-4944-9a62-6eee37294597).

## <a name="generating-the-publish-scripts"></a>Yayımlama betikleri oluşturuluyor

[Bu yönergeleri](/azure/virtual-machines/windows/classic/web-app-visual-studio?toc=%2fazure%2fvirtual-machines%2fwindows%2fclassic%2ftoc.json)izleyerek yeni bir proje oluştururken Web sitenizi barındıran bir sanal makine için yayımlama betikleri oluşturabilirsiniz. Ayrıca, [Azure App Service Web uygulamaları için yayımlama betikleri](/azure/app-service/scripts/app-service-powershell-deploy-github)da oluşturabilirsiniz.

## <a name="scripts-that-visual-studio-generates"></a>Visual Studio 'Nun oluşturduğu betikler

Visual Studio, iki Windows PowerShell dosyası, sanal makineniz veya Web siteniz için bir yayımlama betiği ve betiklerinizde kullanabileceğiniz işlevleri içeren bir modül içeren **Publishscripts** adlı çözüm düzeyinde bir klasör oluşturur. Visual Studio aynı zamanda, dağıttığınız projenin ayrıntılarını belirten JSON biçiminde bir dosya oluşturur.

### <a name="windows-powershell-publish-script"></a>Windows PowerShell yayımlama betiği

Yayımla betiği, bir Web sitesine veya sanal makineye dağıtmaya yönelik belirli yayımlama adımlarını içerir. Visual Studio, Windows PowerShell geliştirmesi için Sözdizimi renklendirmesi sağlar. İşlevler için Yardım kullanılabilir ve değişen gereksinimlerinize uyacak şekilde betikteki işlevleri serbestçe düzenleyebilirsiniz.

### <a name="windows-powershell-module"></a>Windows PowerShell modülü

Visual Studio 'Nun oluşturduğu Windows PowerShell modülü, yayımlama betiğinin kullandığı işlevleri içerir. Bu Azure PowerShell işlevlerinin değiştirilmesi amaçlanmamaktadır. Bkz. [Azure PowerShell'i yükleme ve yapılandırma](/powershell/azure/overview).

### <a name="json-configuration-file"></a>JSON yapılandırma dosyası

JSON dosyası **yapılandırmalar** klasöründe oluşturulur ve Azure 'a tam olarak hangi kaynakların dağıtılacağını belirten yapılandırma verilerini içerir. Visual Studio 'Nun oluşturduğu dosyanın adı, bir Web sitesi oluşturduysanız veya bir sanal makine oluşturduysanız üzerinde name-VM-dev.jsproje üzerinde project-name-WAWS-dev.js. Bir Web sitesi oluştururken oluşturulan JSON yapılandırma dosyasına bir örnek aşağıda verilmiştir. Değerlerin çoğu kendi kendine açıklayıcıdır. Web sitesi adı Azure tarafından oluşturulduğundan proje adınızla eşleşmeyebilir.

```json
{
    "environmentSettings": {
        "webSite": {
            "name": "WebApplication26632",
            "location": "West US"
        },
        "databases": [{
            "connectionStringName": "DefaultConnection",
            "databaseName": "WebApplication26632_db",
            "serverName": "YourDatabaseServerName",
            "user": "sqluser2",
            "password": "",
            "edition": "",
            "size": "",
            "collation": "",
            "location": "West US"
        }]
    }
}
```

Bir sanal makine oluşturduğunuzda, JSON yapılandırma dosyası aşağıdakine benzer şekilde görünür. Bir bulut hizmeti, sanal makine için kapsayıcı olarak oluşturulur. Sanal makine, HTTP ve HTTPS üzerinden Web erişimi için her zamanki uç noktaları ve Web Dağıtımı için uç noktaların yanı sıra yerel makinenizden, uzak masaüstünden ve Windows PowerShell 'de Web sitesinde yayımlama olanağı sağlar.

```json
{
    "environmentSettings": {
        "cloudService": {
            "name": "myusernamevm1",
            "affinityGroup": "",
            "location": "West US",
            "virtualNetwork": "",
            "subnet": "",
            "availabilitySet": "",
            "virtualMachine": {
                "name": "myusernamevm1",
                "vhdImage": "a699494373c04fc0bc8f2bb1389d6106__Win2K8R2SP1-Datacenter-201403.01-en.us-127GB.vhd",
                "size": "Small",
                "user": "vmuser1",
                "password": "",
                "enableWebDeployExtension": true,
                "endpoints": [{
                        "name": "Http",
                        "protocol": "TCP",
                        "publicPort": "80",
                        "privatePort": "80"
                    },
                    {
                        "name": "Https",
                        "protocol": "TCP",
                        "publicPort": "443",
                        "privatePort": "443"
                    },
                    {
                        "name": "WebDeploy",
                        "protocol": "TCP",
                        "publicPort": "8172",
                        "privatePort": "8172"
                    },
                    {
                        "name": "Remote Desktop",
                        "protocol": "TCP",
                        "publicPort": "3389",
                        "privatePort": "3389"
                    },
                    {
                        "name": "Powershell",
                        "protocol": "TCP",
                        "publicPort": "5986",
                        "privatePort": "5986"
                    }
                ]
            }
        },
        "databases": [{
            "connectionStringName": "",
            "databaseName": "",
            "serverName": "",
            "user": "",
            "password": ""
        }],
        "webDeployParameters": {
            "iisWebApplicationName": "Default Web Site"
        }
    }
}
```

Yayımlama betiklerini çalıştırdığınızda ne olacağını değiştirmek için JSON yapılandırmasını düzenleyebilirsiniz. `cloudService`Ve `virtualMachine` bölümleri gereklidir, ancak `databases` gerekmiyorsa bölümünü silebilirsiniz. Visual Studio 'Nun oluşturduğu varsayılan yapılandırma dosyasında boş olan özellikler isteğe bağlıdır; Varsayılan yapılandırma dosyasında değerleri olan özellikler gereklidir.

Azure 'da tek bir üretim sitesi yerine birden çok dağıtım ortamına (yuva olarak bilinir) sahip bir Web siteniz varsa, yuva adını JSON yapılandırma dosyasına Web sitesinin adına ekleyebilirsiniz. Örneğin, **sitem** adlı bir Web siteniz ve **Test** adlı BT için BIR yuva varsa, URI olur `mysite-test.cloudapp.net` , ancak yapılandırma dosyasında kullanılacak doğru ad sitem (test) olur. Bunu yalnızca, Web sitesi ve yuvaları aboneliğinizde zaten mevcutsa yapabilirsiniz. Mevcut değilse, yuvası belirtmeden betiği çalıştırarak Web sitesini oluşturun, ardından [Azure Portal](https://portal.azure.com/)yuvasını oluşturun ve ardından betiği değiştirilen Web sitesi adıyla çalıştırın. Web Apps için dağıtım yuvaları hakkında daha fazla bilgi için, bkz. [Azure App Service Web Apps için hazırlama ortamlarını ayarlama](/azure/app-service/web-sites-staged-publishing).

## <a name="how-to-run-the-publish-scripts"></a>Yayımlama betikleri nasıl çalıştırılır

Daha önce bir Windows PowerShell betiği çalıştırmadıysanız, önce komut dosyalarının çalıştırılmasını sağlamak için yürütme ilkesini ayarlamanız gerekir. İlke, kullanıcıların komut dosyalarını yürütmeyi içeren kötü amaçlı yazılımlara veya virüslere karşı savunmasız olmaları durumunda Windows PowerShell betikleri çalıştırmasını engelleyen bir güvenlik özelliğidir.

### <a name="run-the-script"></a>Betiği çalıştırın

1. Projeniz için Web Dağıtımı paketini oluşturun. Web Dağıtımı Paket, Web sitenize veya sanal makinenize kopyalamak istediğiniz dosyaları içeren sıkıştırılmış bir arşivdir (. zip dosyasıdır). Herhangi bir Web uygulaması için Visual Studio 'da Web Dağıtımı paketleri oluşturabilirsiniz.

   ![Web Dağıtımı Paketi Oluştur](./media/vs-azure-tools-publishing-using-powershell-scripts/IC767885.png)

   Daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'Da Web dağıtım paketi oluşturma](https://msdn.microsoft.com/library/dd465323.aspx). Ayrıca, [Yayımlama betiklerini özelleştirme ve genişletme](#customizing-and-extending-the-publish-scripts)bölümünde açıklandığı gibi Web dağıtımı paketinizin oluşturulmasını otomatik hale getirebilirsiniz.

1. **Çözüm Gezgini**' de, betiğin bağlam menüsünü açın ve ardından **PowerShell ISE ile aç**' ı seçin.
1. Bu bilgisayarda ilk kez Windows PowerShell betikleri çalıştırıyorsanız, yönetici ayrıcalıklarıyla bir komut istemi penceresi açın ve aşağıdaki komutu yazın:

    ```powershell
    Set-ExecutionPolicy RemoteSigned
    ```

1. Aşağıdaki komutu kullanarak Azure 'da oturum açın.

    ```powershell
    Add-AzureAccount
    ```

    İstendiğinde, Kullanıcı adınızı ve parolanızı girin.

    Betiği otomatikleştirdiğiniz zaman, Azure kimlik bilgilerini sağlamaya yönelik bu yöntem işe yaramadığını unutmayın. Bunun yerine, `.publishsettings` kimlik bilgilerini sağlamak için dosyasını kullanmanız gerekir. Yalnızca bir kez, dosyayı Azure 'dan indirmek için **Get-Azuikinci dosya SettingsFile** komutunu kullanın ve bundan sonra dosyayı içeri aktarmak için **Import-Azuyeniden yayımcı SettingsFile** komutunu kullanın. Ayrıntılı yönergeler için bkz. [Azure PowerShell'i yükleme ve yapılandırma](/powershell/azure/overview).

1. Seçim Web uygulamanızı yayımlamadan sanal makine, veritabanı ve Web sitesi gibi Azure kaynakları oluşturmak istiyorsanız, JSON yapılandırma dosyası olarak ayarlanan **-Configuration** bağımsız değişkeniyle birlikte **Publish-WebApplication.ps1** komutunu kullanın. Bu komut satırı, hangi kaynakların oluşturulacağını belirleyen JSON yapılandırma dosyasını kullanır. Diğer komut satırı bağımsız değişkenleri için varsayılan ayarları kullandığından, kaynakları oluşturur, ancak Web uygulamanızı yayımlamaz. – Verbose seçeneği, neler olduğu hakkında daha fazla bilgi sağlar.

    ```powershell
    Publish-WebApplication.ps1 -Verbose –Configuration C:\Path\WebProject-WAWS-dev.json
    ```

1. Komut dosyasını çağırmak ve Web uygulamanızı yayımlamak için aşağıdaki örneklerden birinde gösterildiği gibi **Publish-WebApplication.ps1** komutunu kullanın. Abonelik adı, yayımlama paketi adı, sanal makine kimlik bilgileri veya veritabanı sunucusu kimlik bilgileri gibi diğer bağımsız değişkenlerden herhangi biri için varsayılan ayarları geçersiz kılmanız gerekiyorsa, bu parametreleri belirtebilirsiniz. Yayımlama sürecinin ilerlemesi hakkında daha fazla bilgi görmek için **– verbose** seçeneğini kullanın.

    ```powershell
    Publish-WebApplication.ps1 –Configuration C:\Path\WebProject-WAWS-dev-json `
    –SubscriptionName Contoso `
    -WebDeployPackage C:\Documents\Azure\ADWebApp.zip `
    -DatabaseServerPassword @{Name="dbServerName";Password="adminPassword"} `
    -Verbose
    ```

    Bir sanal makine oluşturuyorsanız, komut aşağıdaki gibi görünür. Bu örnek ayrıca birden çok veritabanı için kimlik bilgilerinin nasıl kullanılacağını gösterir. Bu betiklerin oluşturmakta olduğu sanal makineler için, SSL sertifikası güvenilen bir kök yetkilisinden değildir. Bu nedenle, **– Allowgüvenilmeyen** seçeneğini kullanmanız gerekir.

    ```powershell
    Publish-WebApplication.ps1 `
    -Configuration C:\Path\ADVM-VM-test.json `
    -SubscriptionName Contoso `
    -WebDeployPackage C:\Path\ADVM.zip `
    -AllowUntrusted `
    -VMPassword @{name = "vmUserName"; password = "YourPasswordHere"} `
    -DatabaseServerPassword @{Name="server1";Password="adminPassword1"}, @{Name="server2";Password="adminPassword2"} `
    -Verbose
    ```

    Betik veritabanları oluşturabilir, ancak veritabanı sunucuları oluşturmaz. Bir veritabanı sunucusu oluşturmak istiyorsanız, Azure modülündeki **New-Azuressqldatabaseserver** işlevini kullanabilirsiniz.

## <a name="customizing-and-extending-the-publish-scripts"></a>Yayımlama betiklerini özelleştirme ve genişletme

Yayımlama betiğini ve JSON yapılandırma dosyasını özelleştirebilirsiniz. **AzureWebAppPublishModule. Psm1** Windows PowerShell modülündeki işlevlerin değiştirilmesi amaçlanmamaktadır. Yalnızca farklı bir veritabanı belirtmek veya sanal makinenin bazı özelliklerini değiştirmek istiyorsanız, JSON yapılandırma dosyasını düzenleyin. Projenizin oluşturulmasını ve test edilmesini otomatikleştirmek için betiğin işlevlerini genişletmek istiyorsanız, **Publish-WebApplication.ps1**işlev saplamalarını uygulayabilirsiniz.

Projenizi oluşturmaya otomatik hale getirmek için, `New-WebDeployPackage` Bu kod örneğinde gösterildiği gibi MSBuild 'i çağıran kodu ekleyin. MSBuild komutunun yolu, yüklediğiniz Visual Studio sürümüne bağlı olarak farklılık açmış. Doğru yolu almak için, **Get-MSBuildCmd**işlevini Bu örnekte gösterildiği gibi kullanabilirsiniz.

### <a name="to-automate-building-your-project"></a>Projenizi oluşturmaya otomatik hale getirmek için

1. `$ProjectFile`Parametresini genel param bölümüne ekleyin.

    ```powershell
    [Parameter(Mandatory = $false)]
    [ValidateScript({Test-Path $_ -PathType Leaf})]
    [String]
    $ProjectFile,
    ```

1. İşlevi `Get-MSBuildCmd` betik dosyanıza kopyalayın.

    ```powershell
    function Get-MSBuildCmd
    {
            process
    {

                $path =  Get-ChildItem "HKLM:\SOFTWARE\Microsoft\MSBuild\ToolsVersions\" |
                                    Sort-Object {[double]$_.PSChildName} -Descending |
                                    Select-Object -First 1 |
                                    Get-ItemProperty -Name MSBuildToolsPath |
                                    Select -ExpandProperty MSBuildToolsPath

                $path = (Join-Path -Path $path -ChildPath 'msbuild.exe')

            return Get-Item $path
        }
    }
    ```

1. `New-WebDeployPackage`Aşağıdaki kodla değiştirin ve satır oluşturulurken yer tutucuları değiştirin `$msbuildCmd` . Bu kod, Visual Studio 2015 içindir. Visual Studio 2017 kullanıyorsanız, **VisualStudioVersion** özelliğini `15.0` ( `12.0` Visual Studio 2013 için) olarak değiştirin.

    ```powershell
    function New-WebDeployPackage
    {
        #Write a function to build and package your web application
    ```

    Web uygulamanızı derlemek için MsBuild.exe kullanın. Yardım için bkz. MSBuild komut satırı başvurusu: [http://go.microsoft.com/fwlink/?LinkId=391339](https://msdn.microsoft.com/library/ms164311.aspx)

    ```powershell
    Write-VerboseWithTime 'Build-WebDeployPackage: Start'

    $msbuildCmd = '"{0}" "{1}" /T:Rebuild;Package /P:VisualStudioVersion=14.0 /p:OutputPath="{2}\MSBuildOutputPath" /flp:logfile=msbuild.log,v=d' -f (Get-MSBuildCmd), $ProjectFile, $scriptDirectory

    Write-VerboseWithTime ('Build-WebDeployPackage: ' + $msbuildCmd)
    ```

### <a name="start-execution-of-the-build-command"></a>Build komutunun yürütülmesini Başlat

```powershell
$job = Start-Process cmd.exe -ArgumentList('/C "' + $msbuildCmd + '"') -WindowStyle Normal -Wait -PassThru

if ($job.ExitCode -ne 0) {
    throw('MsBuild exited with an error. ExitCode:' + $job.ExitCode)
}

#Obtain the project name
$projectName = (Get-Item $ProjectFile).BaseName

#Construct the path to web deploy zip package
$DeployPackageDir =  '.\MSBuildOutputPath\_PublishedWebsites\{0}_Package\{0}.zip' -f $projectName

#Get the full path for the web deploy zip package. This is required for MSDeploy to work
$WebDeployPackage = Resolve-Path –LiteralPath $DeployPackageDir

Write-VerboseWithTime 'Build-WebDeployPackage: End'

return $WebDeployPackage
}
```

1. `New-WebDeployPackage`Bu satırdan önce işlevi çağırın: `$Config = Read-ConfigFile $Configuration` Web uygulamaları veya `$Config = Read-ConfigFile $Configuration -HasWebDeployPackage:([Bool]$WebDeployPackage)` sanal makineler için.

    ```powershell
    if($ProjectFile)
    {
    $WebDeployPackage = New-WebDeployPackage
    }
    ```

1. `$Project`Aşağıdaki örnekte gösterildiği gibi bağımsız değişkeni geçirerek komut satırından özelleştirilmiş betiği çağırın:

    ```powershell
    .\Publish-WebApplicationVM.ps1 -Configuration .\Configurations\WebApplication5-VM-dev.json `
    -ProjectFile ..\WebApplication5\WebApplication5.csproj `
    -VMPassword @{Name="VMUser";Password="Test.123"} `
    -AllowUntrusted `
    -Verbose
    ```

    Uygulamanızın testini otomatik hale getirmek için kod ekleyin `Test-WebApplication` . Bu işlevlerin çağrıldığı **Publish-WebApplication.ps1** satırlarda açıklama eklediğinizden emin olun. Uygulama sağlamazsanız, projenizi Visual Studio ile el ile oluşturabilir ve ardından yayımlama betiğini çalıştırarak Azure 'da yayımlayabilirsiniz.

## <a name="publishing-function-summary"></a>Yayımlama işlevi Özeti
Windows PowerShell komut isteminde kullanabileceğiniz işlevler hakkında yardım almak için komutunu kullanın `Get-Help function-name` . Yardım, parametre yardımını ve örnekleri içerir. Aynı yardım metni, **AzureWebAppPublishModule. psm1** ve **Publish-WebApplication.ps1**komut dosyası kaynak dosyalarında de bulunur. Betik ve yardım, Visual Studio dilinizde yerelleştirilmiştir.

**AzureWebAppPublishModule**

| İşlev adı | Description |
| --- | --- |
| Add-Azuressqldatabase |Yeni bir Azure SQL veritabanı oluşturur. |
| Add-Azuressqldatabases |Visual Studio 'Nun oluşturduğu JSON yapılandırma dosyasındaki değerlerden Azure SQL veritabanları oluşturur. |
| Add-AzureVM |Bir Azure sanal makinesi oluşturur ve dağıtılan VM 'nin URL 'sini döndürür. İşlevi önkoşulları ayarlar ve yeni bir sanal makine oluşturmak için **New-AzureVM** Işlevini (Azure modülü) çağırır. |
| Add-AzureVMEndpoints |Bir sanal makineye yeni giriş uç noktaları ekler ve sanal makineyi yeni uç noktayla döndürür. |
| Add-AzureVMStorage |Geçerli abonelikte yeni bir Azure depolama hesabı oluşturur. Hesabın adı "DevTest" ile başlar ve ardından benzersiz bir alfasayısal dize gelir. İşlevi, yeni depolama hesabının adını döndürür. Yeni depolama hesabı için bir konum ya da benzeşim grubu belirtin. |
| Add-AzureWebsite |Belirtilen ad ve konuma sahip bir Web sitesi oluşturur. Bu işlev, Azure modülündeki **New-AzureWebsite** işlevini çağırır. Abonelik, belirtilen ada sahip bir Web sitesini zaten içermiyorsa, bu işlev Web sitesini oluşturur ve bir Web sitesi nesnesi döndürür. Aksi takdirde, döndürür `$null` . |
| Yedekleme-abonelik |Geçerli Azure aboneliğini `$Script:originalSubscription` betik kapsamındaki değişkene kaydeder. Bu işlev, geçerli Azure aboneliğini (tarafından alındığı şekilde `Get-AzureSubscription -Current` ) ve depolama hesabını ve bu komut dosyası (değişkende depolanan `$UserSpecifiedSubscription` ) ve depolama hesabını komut dosyası kapsamında değiştiren aboneliği kaydeder. Değerleri kaydederek, `Restore-Subscription` geçerli durum değiştiyse orijinal geçerli aboneliği ve depolama hesabını geçerli duruma geri yüklemek için gibi bir işlevi kullanabilirsiniz. |
| Find-AzureVM |Belirtilen Azure sanal makinesini alır. |
| Format-DevTestMessageWithTime |Bir iletinin tarihini ve saatini önüne ekleyin. Bu işlev, hataya ve ayrıntılı akışlara yazılan iletiler için tasarlanmıştır. |
| Get-Azuressqldatabaseconnectionstring |Bir Azure SQL veritabanına bağlanmak için bir bağlantı dizesi ayrıştırır. |
| Get-AzureVMStorage |*Belirtilen konum veya benzeşim grubundaki "DevTest" (büyük/küçük harf duyarsız) adlı ilk depolama hesabının adını döndürür. "DevTest*" depolama hesabı konum veya benzeşim grubuyla eşleşmezse, işlev onu yoksayar. Bir konum ya da benzeşim grubu belirtin. |
| Get-MSDeployCmd |MsDeploy.exe aracını çalıştırmak için bir komut döndürür. |
| New-AzureVMEnvironment |Abonelikte JSON yapılandırma dosyasındaki değerlerle eşleşen bir sanal makine bulur veya oluşturur. |
| Yayımla-WebPackage |MsDeploy.exe ve bir Web yayımlama paketi kullanır. Bir Web sitesine kaynak dağıtmak için zip dosyası. Bu işlev herhangi bir çıktı oluşturmaz. MSDeploy.exe çağrısı başarısız olursa, işlev bir özel durum atar. Daha ayrıntılı çıkış almak için **-verbose** seçeneğini kullanın. |
| Publish-WebPackageToVM |Parametre değerlerini doğrular ve ardından **Publish-WebPackage** işlevini çağırır. |
| Okuma-ConfigFile |JSON yapılandırma dosyasını doğrular ve seçilen değerlerin bir karma tablosu döndürür. |
| Geri yükleme-abonelik |Geçerli aboneliği orijinal aboneliğe sıfırlar. |
| Test-AzureModule |`$true`Yüklü Azure modülü sürümü 0.7.4 veya daha yeni bir sürümse döndürür. `$false`Modül yüklü değilse veya önceki bir sürümse döndürür. Bu işlevin parametresi yok. |
| Test-Azuremodutaversion |`$true`Azure modülünün sürümünün 0.7.4 veya sonraki bir sürümü olup olmadığını döndürür. `$false`Modül yüklü değilse veya önceki bir sürümse döndürür. Bu işlevin parametresi yok. |
| Test-HttpsUrl |Giriş URL 'sini bir System. Uri nesnesine dönüştürür. `$True`URL mutlak ise ve düzeni https ise döndürür. `$false`URL göreli ise, DÜZENININ https olmaması veya giriş dizesinin BIR URL 'ye dönüştürülemediği, döndürür. |
| Test-üye |`$true`Bir özellik veya yöntemin nesnenin üyesi olup olmadığını döndürür. Aksi takdirde, döndürür `$false` . |
| Write-ErrorWithTime |Geçerli zamana ön eki eklenmiş bir hata iletisi yazar. Bu işlev, iletiyi hata akışına yazmadan önce saati sonuna eklemek için **Format-DevTestMessageWithTime** işlevini çağırır. |
| Write-HostWithTime |Geçerli zamanı ön eki olan ana bilgisayar programına (**yazma ana bilgisayar**) bir ileti yazar. Ana bilgisayar programına yazma etkisi değişir. Windows PowerShell 'i barındıran çoğu program, bu iletileri standart çıktıya yazar. |
| Write-VerboseWithTime |Geçerli zamanı ön eki olan ayrıntılı bir ileti yazar. **Write-Verbose**' i çağırdığı için ileti yalnızca komut dosyası **verbose** parametresiyle çalıştırıldığında veya **VerbosePreference** tercihi **devam**olarak ayarlandığında görüntülenir. |

**Yayımla-WebApplication**

| İşlev adı | Description |
| --- | --- |
| New-AzureWebApplicationEnvironment |Bir Web sitesi veya sanal makine gibi Azure kaynakları oluşturur. |
| New-WebDeployPackage |Bu işlev uygulanmadı. Projenizi derlemek için bu işleve komutlar ekleyebilirsiniz. |
| Yayımla-AzureWebApplication |Bir Web uygulamasını Azure 'da yayımlar. |
| Yayımla-WebApplication |Visual Studio Web projesi için Web Apps, sanal makineler, SQL veritabanları ve depolama hesapları oluşturur ve dağıtır. |
| Test-WebApplication |Bu işlev uygulanmadı. Uygulamanızı test etmek için bu işlevde komutlar ekleyebilirsiniz. |

## <a name="next-steps"></a>Sonraki adımlar
[Windows PowerShell Ile komut](/powershell/scripting/overview) dosyasını okuyarak ve [betik merkezindeki](https://azure.microsoft.com/documentation/scripts/)diğer Azure PowerShell betikleri ' ni okuyarak PowerShell betiği hakkında daha fazla bilgi edinin.
