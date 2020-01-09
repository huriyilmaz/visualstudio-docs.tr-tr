---
title: Çevrimdışı yükleme için gerekli sertifikaları yükleme
description: Visual Studio'yu çevrimdışı yükleme için sertifikaları yüklemeyi öğrenin.
ms.date: 08/08/2019
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 9750A3F3-89C7-4A8F-BA75-B0B06BD772C2
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 4db5de36e9982ac3d708f8826f441751c2fd0891
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594077"
---
# <a name="install-certificates-required-for-visual-studio-offline-installation"></a>Visual Studio'yu çevrimdışı yükleme için gerekli sertifikaları yükleme

Visual Studio, İnternet'e bağlı bir makinede, birçok bileşen düzenli olarak güncelleştirilen bu yana yüklenmesi için birincil olarak tasarlanmıştır. Ancak, bazı ek adımlar, Visual Studio ortamında çalışan bir yerde dağıtmak mümkün mü internet bağlantısı kullanılamıyor.

Visual Studio Kurulum altyapısı güvenilen yalnızca içeriği yükler. Bunu Authenticode imzaları içerik indiriliyor ve yüklemeden önce tüm içeriği güvenilen doğrulama denetleyerek yapar. Bu ortamınızı indirme konumuna burada tehlikeye saldırılarına karşı güvenli tutar. Visual Studio Kurulum, bu nedenle birkaç standart Microsoft kök ve ara sertifika yüklü olmasını gerektirir ve yukarı başından bu yana bir kullanıcının makine üzerinde. İmzalama sertifikaları genellikle makine Windows Update ile güncel tutulmuştur, güncel demektir. Makinenin internet'e bağlı olup olmadığını, yükleme sırasında Visual Studio gerektiğinde dosya imzaları doğrulamak sertifikaları yenileme. Makine çevrimdışı ise, sertifikalar olmalıdır başka bir şekilde yenilendi.

## <a name="how-to-refresh-certificates-when-offline"></a>Çevrimdışıyken sertifikaları yenileme

Yükleme veya çevrimdışı bir ortamda sertifikaları güncelleştirme için üç seçenek vardır.

### <a name="option-1---manually-install-certificates-from-a-layout-folder"></a>1\. seçenek - sertifikaları bir düzen klasöründen el ile yükleyin

::: moniker range="vs-2017"

Bir ağ düzeni oluşturduğunuzda, gerekli sertifikaları Sertifikalar klasörüne yüklenir. Daha sonra el ile sertifikalar tarafından her bir sertifika dosyasını çift tıklatarak ve ardından Sertifika Yöneticisi Sihirbazı yükleyebilirsiniz. İçin bir parola istenirse, boş bırakın.

**Güncelleştirme**: Visual Studio 2017 sürüm 15,8 önizleme 2 veya daha sonra el ile sertifikalar her sertifika dosyaları sağ tıklayarak yükleyebilirsiniz sertifikayı yükle, seçtikten sonra Sertifika Yöneticisi sihirbazda ilerleyin.

::: moniker-end

::: moniker range="vs-2019"

Bir ağ düzeni oluşturduğunuzda, gerekli sertifikaları Sertifikalar klasörüne yüklenir. Sertifika dosyalarının her birine sağ tıklayıp sertifikayı yükler ' i seçip Sertifika Yöneticisi Sihirbazı ' na tıklayarak sertifikaları el ile yükleyebilirsiniz. İçin bir parola istenirse, boş bırakın.

::: moniker-end

### <a name="option-2---distribute-trusted-root-certificates-in-an-enterprise-environment"></a>2\. seçenek - güvenilen kök dağıtmak bir kuruluş ortamında sertifikaları

En son kök sertifikaların olması değil çevrimdışı makinelerle kuruluşlar için bir yönetici yönergeleri kullanabilirsiniz [yapılandırma Güvenilen Kökleri ve izin verilmeyen sertifikaları](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn265983(v=ws.11)) bunları güncelleştirmek için sayfa.

### <a name="option-3---install-certificates-as-part-of-a-scripted-deployment-of-visual-studio"></a>Seçenek 3 - bir komut dosyası dağıtım Visual Studio'nun bir parçası olarak yükleme sertifikaları

Visual Studio'nun istemci iş istasyonları için çevrimdışı bir ortamda dağıtım komut dosyası oluşturma, şu adımları izlemelidir:

::: moniker range="vs-2017"

1. Kopyalama [Sertifika Yöneticisi Aracı](/dotnet/framework/tools/certmgr-exe-certificate-manager-tool) (certmgr.exe) yükleme paylaşımına (örneğin, \\server\share\vs2017). Certmgr.exe dahil değildir ancak Windows kendisini bir parçası olarak olarak kullanılabilir parçası [Windows SDK'sı](https://developer.microsoft.com/windows/downloads/windows-10-sdk).

2. Bir toplu iş dosyası aşağıdaki komutlarla oluşturun:

   ```cmd
   certmgr.exe -add -c certificates\manifestSignCertificates.p12 -n "Microsoft Code Signing PCA 2011" -s -r LocalMachine CA

   certmgr.exe -add -c certificates\manifestSignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root

   certmgr.exe -add -c certificates\manifestCounterSignCertificates.p12 -n "Microsoft Time-Stamp PCA 2010" -s -r LocalMachine CA

   certmgr.exe -add -c certificates\manifestCounterSignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root

   certmgr.exe -add -c certificates\vs_installer_opc.SignCertificates.p12 -n "Microsoft Code Signing PCA" -s -r LocalMachine CA

   certmgr.exe -add -c certificates\vs_installer_opc.SignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root
   ```

   **Güncelleştirme**: Visual Studio 2017 sürüm 15,8 önizleme 2 veya sonraki sürümü oluşturma toplu iş dosyası aşağıdaki komutlarla:

   ```cmd
   certmgr.exe -add [layout path]\certificates\manifestRootCertificate.cer -n "Microsoft Root Certificate Authority 2011" -s -r LocalMachine root

   certmgr.exe -add [layout path]\certificates\manifestCounterSignRootCertificate.cer -n "Microsoft Root Certificate Authority 2010" -s -r LocalMachine root

   certmgr.exe -add [layout path]\certificates\vs_installer_opc.RootCertificate.cer -n "Microsoft Root Certificate Authority" -s -r LocalMachine root
   ```
   
   Alternatif olarak, aşağıdaki komutlarla Windows ile birlikte gelen certutil. exe ' yi kullanan bir toplu işlem dosyası oluşturun:
   
      ```cmd
   certutil.exe -addstore -f "Root" "[layout path]\certificates\manifestRootCertificate.cer"

   certutil.exe -addstore -f "Root" "[layout path]\certificates\manifestCounterSignRootCertificate.cer"

   certutil.exe -addstore -f "Root" "[layout path]\certificates\vs_installer_opc.RootCertificate.cer"
   ```

3. Toplu iş dosyası, istemciye dağıtın. Bu komutu yükseltilmiş bir işlemden çalıştırılmalıdır.

::: moniker-end

::: moniker range="vs-2019"

1. [Sertifika Yöneticisi aracını](/dotnet/framework/tools/certmgr-exe-certificate-manager-tool) (certmgr. exe) yükleme paylaşımında (örneğin, \\server\share\vs2019) kopyalayın. Certmgr.exe dahil değildir ancak Windows kendisini bir parçası olarak olarak kullanılabilir parçası [Windows SDK'sı](https://developer.microsoft.com/windows/downloads/windows-10-sdk).

2. Bir toplu iş dosyası aşağıdaki komutlarla oluşturun:

   ```cmd
   certmgr.exe -add [layout path]\certificates\manifestRootCertificate.cer -n "Microsoft Root Certificate Authority 2011" -s -r LocalMachine root

   certmgr.exe -add [layout path]\certificates\manifestCounterSignRootCertificate.cer -n "Microsoft Root Certificate Authority 2010" -s -r LocalMachine root

   certmgr.exe -add [layout path]\certificates\vs_installer_opc.RootCertificate.cer -n "Microsoft Root Certificate Authority" -s -r LocalMachine root
   ```
   
   Alternatif olarak, aşağıdaki komutlarla Windows ile birlikte gelen certutil. exe ' yi kullanan bir toplu işlem dosyası oluşturun:
   
      ```cmd
   certutil.exe -addstore -f "Root" "[layout path]\certificates\manifestRootCertificate.cer

   certutil.exe -addstore -f "Root" [layout path]\certificates\manifestCounterSignRootCertificate.cer"

   certutil.exe -addstore -f "Root" "[layout path]\certificates\vs_installer_opc.RootCertificate.cer"
   ```

3. Toplu iş dosyası, istemciye dağıtın. Bu komutu yükseltilmiş bir işlemden çalıştırılmalıdır.

::: moniker-end

## <a name="what-are-the-certificates-files-in-the-certificates-folder"></a>Sertifikaları klasöründe bulunan sertifikaları dosyaları nelerdir?

::: moniker range="vs-2017"

Üç. P12 bu klasördeki dosyalar her bir ara sertifika ve bir kök sertifikası içerir. Windows Update ile güncel çoğu sistemleri, bu sertifikaların yüklü sahiptir.

* **ManifestSignCertificates.p12** içerir:
  * Ara Sertifika: **Microsoft kod imzalama PCA 2011**
    * Gerekli değildir. Varsa, bazı senaryolarda performansı artırır.
  * Kök sertifika: **Microsoft kök sertifika yetkilisi 2011**
    * Windows 7 Service Pack 1 sistemlerinde yüklü en son Windows güncelleştirmelerini sahip olmaması gerekir.
* **ManifestCounterSignCertificates.p12** içerir:
  * Ara Sertifika: **Microsoft zaman damgası PCA 2010**
    * Gerekli değildir. Varsa, bazı senaryolarda performansı artırır.
  * Kök sertifika: **Microsoft kök sertifika yetkilisi 2010**
    * En son Windows güncelleştirmelerini yüklü olmayan Windows 7 Service Pack 1 sistemler için gereklidir.
* **Vs_installer_opc. SignCertificates.p12** içerir:
  * Ara Sertifika: **Microsoft kod imzalama PCA**
    * Tüm sistemler için gereklidir. Tüm güncelleştirmelerin Windows Update'ten uygulandığı sistemleri bu sertifikayı olmayabilir unutmayın.
  * Kök sertifika: **Microsoft kök sertifika yetkilisi**
    * Gerekli. Bu sertifika, Windows 7 veya üzerini çalıştıran sistemleriyle birlikte gelir.

**Güncelleştirme**: sistemde yüklenmesi için Visual Studio 2017 sürüm 2 veya üzeri 15,8 önizleme, Visual Studio yükleyicisi, yalnızca kök gerektirir sertifikaları. Bu sertifikalar. p12 yerine. cer dosyalarında depolanır.

::: moniker-end

::: moniker range="vs-2019"

* **Manifestsigncertificates. cer** şunları içerir:
  * Kök sertifika: **Microsoft kök sertifika yetkilisi 2011**
    * Windows 7 Service Pack 1 sistemlerinde yüklü en son Windows güncelleştirmelerini sahip olmaması gerekir.
* **Manifestcountersigncertificates. cer** şunları içerir:
  * Kök sertifika: **Microsoft kök sertifika yetkilisi 2010**
    * En son Windows güncelleştirmelerini yüklü olmayan Windows 7 Service Pack 1 sistemler için gereklidir.
* **Vs_installer_opc. SignCertificates. cer** şunları içerir:
  * Kök sertifika: **Microsoft kök sertifika yetkilisi**
    * Gerekli. Bu sertifika, Windows 7 veya üzerini çalıştıran sistemleriyle birlikte gelir.

Visual Studio Yükleyicisi, sisteme yalnızca kök sertifikaların yüklenmesini gerektirir.

::: moniker-end

## <a name="why-are-the-certificates-from-the-certificates-folder-not-installed-automatically"></a>Neden sertifikaları otomatik olarak yüklü olmayan sertifikalar klasöründen?

Bir imza bir çevrimiçi ortamda doğrulandığında, Windows API'ları indirmek ve sertifikaları sisteme eklemek için kullanılır. Bu işlem sırasında sertifika güvenilir değil ve yönetim ayarları izin doğrulaması gerçekleşir. Bu doğrulama sürecini en çevrimdışı ortamlarda gerçekleştirilemez. Sertifikaları el ile yükleme sertifikaları Güvenilen ve kendi kuruluşları güvenlik ilkesine uyum sağlamak kuruluş yöneticileri sağlar.

## <a name="checking-if-certificates-are-already-installed"></a>Sertifika zaten yüklü olup olmadığını denetleme

Yükleme sistemde denetleyin yollarından biri, şu adımları takip etmektir:

1. Çalıştırma **mmc.exe**.<br/>
  a. **Dosya**' ya ve sonra **ek bileşen Ekle/Kaldır**' ı seçin.<br/>
  b. Çift **sertifikaları**seçin **bilgisayar hesabı**ve ardından **sonraki**.<br/>
  c. Seçin **yerel bilgisayar**, tıklayın **son**ve ardından **Tamam**.<br/>
  d. Genişletin **sertifikalar (yerel bilgisayar)** .<br/>
  e. Genişletin **güvenilen kök sertifika yetkilileri**ve ardından **sertifikaları**.<br/>
    * Gerekli kök sertifika için bu listeyi kontrol edin.<br/>

   f. Genişletin **Ara Sertifika Yetkilileri**ve ardından **sertifikaları**.<br/>
    * Gerekli Ara sertifikaları için bu listeyi kontrol edin.<br/>

2. **Dosya**' ya ve sonra **ek bileşen Ekle/Kaldır**' ı seçin.<br/>
  a. Çift **sertifikaları**seçin **kullanıcı hesabım**, tıklayın **son**ve ardından **Tamam**.<br/>
  b. Genişletin **Sertifikalar – Geçerli kullanıcı**.<br/>
  c. Genişletin **Ara Sertifika Yetkilileri**ve ardından **sertifikaları**.<br/>
    * Gerekli Ara sertifikaları için bu listeyi kontrol edin.<br/>

Sertifika adları içinde değilse **çıkarılan** sütunları yüklü olması gerekir.  Bir ara sertifika yalnızca içinde ise **geçerli kullanıcının** ara sertifika deposu, sonra da günlüğe kaydedilen kullanıcı için kullanılabilir. Diğer kullanıcılar için yüklemeniz gerekebilir.

## <a name="install-visual-studio"></a>Visual Studio Yükle

Sertifikalar'ı yükledikten sonra Visual Studio'nun dağıtım yönergeleri kullanarak devam edebilirsiniz [ağ yüklemesinden dağıtma](create-a-network-installation-of-visual-studio.md#deploy-from-a-network-installation) sayfası "oluşturma Visual Studio'nun bir ağ yükleme" bölümü.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio'yu yükleyin](install-visual-studio.md)
* [Visual Studio Yönetici Kılavuzu](visual-studio-administrator-guide.md)
* [Komut satırı parametrelerini kullanarak Visual Studio'yu yükleme](use-command-line-parameters-to-install-visual-studio.md)
* [Visual Studio iş yükü ve bileşen kimlikleri](workload-and-component-ids.md)
