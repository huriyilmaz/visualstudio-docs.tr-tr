---
title: Çevrimdışı yükleme için sertifikaları yükleme
description: Çevrimdışı yükleme için sertifika yükleme hakkında Visual Studio öğrenin.
ms.date: 03/29/2021
ms.topic: how-to
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 9750A3F3-89C7-4A8F-BA75-B0B06BD772C2
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: e53989e5872d7bb34317285ce022d630b2de0835
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129968102"
---
# <a name="install-certificates-required-for-visual-studio-offline-installation"></a>Çevrimdışı yükleme için Visual Studio sertifikaları yükleme

Visual Studio, birçok bileşen düzenli olarak güncelleştirildiğinden, birincil olarak İnternet'e bağlı bir makineye yüklenmek üzere tasarlanmıştır. Ancak, bazı ek adımlarla, çalışan bir İnternet Visual Studio kullanılamayan bir ortamda sanal ağ dağıtımı yapmak mümkündür.

Yükleme Visual Studio altyapısı yalnızca güvenilen içeriği yüklür. Bunu, indirilen içeriğin Authenticode imzalarını kontrol ederek ve yüklemeden önce tüm içeriğin güvenilir olduğunu doğrular. Bu, ortamınızı indirme konumunun tehlikeye atılmış olduğu saldırılara karşı güvende tutar. Visual Studio nedenle, bir kullanıcının makinesine birkaç standart Microsoft kök ve ara sertifikasının yüklü ve güncel olması gerekir. Makine Güncelleştirme ile güncel Windows, imzalama sertifikaları genellikle günceldir. Makine İnternet'e bağlı ise, yükleme sırasında Visual Studio imzaları doğrulamak için sertifikaları yeniler. Makine çevrimdışıysa sertifikaların başka bir şekilde yenilenmesi gerekir.

## <a name="how-to-refresh-certificates-when-offline"></a>Çevrimdışıyken sertifikaları yenileme

Çevrimdışı bir ortamda sertifika yüklemek veya güncelleştirmek için üç seçenek vardır.

### <a name="option-1---manually-install-certificates-from-a-layout-folder"></a>1. Seçenek - Bir düzen klasöründen sertifikaları el ile yükleme

::: moniker range="vs-2017"

Bir ağ düzeni [veya yerel](../install/create-a-network-installation-of-visual-studio.md) bir çevrimdışı [önbellek sanız,](../install/create-an-offline-installation-of-visual-studio.md)gerekli sertifikalar Sertifikalar klasörüne indirilir. Ardından, sertifika dosyalarının her biri çift tıklayarak ve ardından Sertifika Yöneticisi sihirbazına tıklayarak sertifikaları el ile yükleyebilirsiniz. Parola istenirse boş bırakın.

**Güncelleştirme:** Visual Studio 2017 sürüm 15.8 Önizleme 2 veya sonraki sürümler için, sertifika dosyalarının her biri sağ tıklar, Sertifika Yükle'yi seçerek ve ardından Sertifika Yöneticisi sihirbazına tıklayarak sertifikaları el ile yükleyebilirsiniz.

::: moniker-end

::: moniker range=">=vs-2019"

Bir ağ düzeni [veya yerel](../install/create-a-network-installation-of-visual-studio.md) bir çevrimdışı [önbellek sanız,](../install/create-an-offline-installation-of-visual-studio.md)gerekli sertifikalar Sertifikalar klasörüne indirilir. Sertifika dosyalarının her biri sağ tıklar, SertifikaYı Yükle'yi seçer ve ardından Sertifika Yöneticisi sihirbazına tıklayarak sertifikaları el ile yükleyebilirsiniz. Parola istenirse boş bırakın.

::: moniker-end

### <a name="option-2---distribute-trusted-root-certificates-in-an-enterprise-environment"></a>2. Seçenek - Güvenilen kök sertifikalarını kurumsal bir ortamda dağıtma

En son kök sertifikalara sahip çevrimdışı makinelere sahip kuruluşlar için, [](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn265983(v=ws.11)) bir yönetici Güvenilen Kökleri Ve Izin Verilmeyen Sertifikaları Yapılandırma sayfasındaki yönergeleri kullanarak bunları güncelleştirebilirsiniz.

### <a name="option-3---install-certificates-as-part-of-a-scripted-deployment-of-visual-studio"></a>3. Seçenek - Sertifikalar için betik dağıtımı kapsamında Visual Studio

İstemci iş istasyonlarına çevrimdışı ortamda Visual Studio betik yazıyorsanız şu adımları izlemalısınız:

1. Sertifika Yöneticisi [Aracı'nı](/dotnet/framework/tools/certmgr-exe-certificate-manager-tool) (certmgr.exe) ağ düzenine veya yerel önbellek yükleme konuma kopyalayın. Certmgr.exe, kendi Windows parçası olarak dahil değildir, ancak Windows [SDK'sı kapsamında kullanılabilir.](https://developer.microsoft.com/windows/downloads/windows-10-sdk)

2. Aşağıdaki komutlarla bir toplu iş dosyası oluşturun:

   ```shell
   certmgr.exe -add [layout path]\certificates\manifestRootCertificate.cer -n "Microsoft Root Certificate Authority 2011" -s -r LocalMachine root

   certmgr.exe -add [layout path]\certificates\manifestCounterSignRootCertificate.cer -n "Microsoft Root Certificate Authority 2010" -s -r LocalMachine root

   certmgr.exe -add [layout path]\certificates\vs_installer_opc.RootCertificate.cer -n "Microsoft Root Certificate Authority 2010" -s -r LocalMachine root
   ```
   
   Alternatif olarak, aşağıdaki komutlarla birlikte certutil.exe kullanarak Windows bir toplu iş dosyası oluşturun:
   
      ```shell
   certutil.exe -addstore -f "Root" "[layout path]\certificates\manifestRootCertificate.cer"

   certutil.exe -addstore -f "Root" "[layout path]\certificates\manifestCounterSignRootCertificate.cer"

   certutil.exe -addstore -f "Root" "[layout path]\certificates\vs_installer_opc.RootCertificate.cer"
   ```

3. Toplu iş dosyasını istemciye dağıtın. Bu komut yükseltilmiş bir işlemden çalıştırıldı.

## <a name="what-are-the-certificates-files-in-the-certificates-folder"></a>Sertifikalar klasöründeki sertifika dosyaları nedir?

* **manifestRootCertificate.cer şunları** içerir:
  * Kök sertifika: **Microsoft Kök Sertifika Yetkilisi 2011**
* **manifestCounterSignRootCertificate.cer** ve **vs_installer_opc. RootCertificate.cer şunları** içerir:
  * Kök sertifika: **Microsoft Kök Sertifika Yetkilisi 2010**
 
Bu Visual Studio Yükleyicisi yalnızca kök sertifikaların sistemde yüklü olması gerekir. Bu sertifikaların hepsi, en son Windows güncelleştirmeleri yüklü olan Windows 7 Service Pack 1 Windows gereklidir.

## <a name="why-are-the-certificates-from-the-certificates-folder-not-installed-automatically"></a>Sertifikalar klasöründeki sertifikalar neden otomatik olarak yüklenmez?

Çevrimiçi bir ortamda bir imza doğrulandığında, sertifikaları Windows ve sisteme eklemek için api'ler kullanılır. Sertifikanın güvenilir olduğunu ve yönetim ayarları aracılığıyla izin verildiğini doğrulama işlemi bu işlem sırasında gerçekleşir. Bu doğrulama işlemi çoğu çevrimdışı ortamda olamaz. Sertifikaları el ile yüklemek, kuruluş yöneticilerinin sertifikaların güvenilir olduğundan emin olmasını ve kuruluşlarının güvenlik ilkesine uygun olmasını sağlar.

## <a name="checking-if-certificates-are-already-installed"></a>Sertifikaların zaten yüklü olup olduğunu denetleme

Yükleme sistemini denetlemenin bir yolu şu adımları takip etmektir:

1. **mmc.exe.**<br/>
  a. Dosya **'ya** tıklayın ve ardından **Ek Bileşen Ekle/Kaldır'ı seçin.**<br/>
  b. Sertifikalar'a **çift tıklayın,** Bilgisayar **hesabı'ı seçin ve** ardından Sonraki'ye **tıklayın.**<br/>
  c. Yerel **bilgisayar'ı seçin,** **Son'a ve** ardından Tamam'a **tıklayın.**<br/>
  d. Sertifikalar **(Yerel Bilgisayar) 'i genişletin.**<br/>
  e. **'Güvenilen Kök Sertifika Yetkilileri** genişletin ve Sertifikalar'ı **seçin.**<br/>
    * Gerekli kök sertifikalar için bu listeyi kontrol edin.<br/>

   f. Ara **Sertifika Yetkilileri'ne genişletin** ve sertifikalar'ı **seçin.**<br/>
    * Gerekli ara sertifikalar için bu listeyi kontrol edin.<br/>

2. Dosya **'ya** tıklayın ve ardından **Ek Bileşen Ekle/Kaldır'ı seçin.**<br/>
  a. Sertifikalar'a **çift tıklayın,** Kullanıcı **hesabım'ı seçin,** Son'a **ve** ardından Tamam'a **tıklayın.**<br/>
  b. Sertifikalar **– Geçerli Kullanıcı'ya genişletin.**<br/>
  c. Ara **Sertifika Yetkilileri'ne genişletin** ve sertifikalar'ı **seçin.**<br/>
    * Gerekli ara sertifikalar için bu listeyi kontrol edin.<br/>

Sertifika adları Verilenler **sütunlarında yer alıyorsa,** bunların yüklü olması gerekir.  Bir ara sertifika yalnızca  Geçerli Kullanıcı Ara Sertifika depolamada bulunuyorsa, yalnızca oturum açmış olan kullanıcı tarafından kullanılabilir. Bunu diğer kullanıcılar için yüklemeniz gerekebilirsiniz.

## <a name="install-visual-studio"></a>Visual Studio'yu yükleme

Sertifikaları istemci makinesine yükledikten sonra, yerel önbellekten [Visual Studio](../install/create-an-offline-installation-of-visual-studio.md#step-3---install-visual-studio-from-the-local-cache)yüklemeye veya ağ [](create-a-network-installation-of-visual-studio.md#deploy-from-a-network-installation) düzeni paylaşımından Visual Studio istemci makinesine dağıtmaya hazır olursanız.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Ağ yüklemesi oluşturma Visual Studio](../install/create-a-network-installation-of-visual-studio.md)
* [Visual Studio’nun çevrimdışı yüklemesini oluşturma](../install/create-an-offline-installation-of-visual-studio.md)
* [Visual Studio yönetici kılavuzu](visual-studio-administrator-guide.md)
* [Komut satırı parametrelerini kullanarak Visual Studio'yu yükleme](use-command-line-parameters-to-install-visual-studio.md)

