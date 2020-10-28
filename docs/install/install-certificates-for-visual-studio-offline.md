---
title: Çevrimdışı yükleme için sertifikaları yükleme
description: Visual Studio çevrimdışı yüklemesi için sertifikaları yüklemeyi öğrenin.
ms.date: 08/08/2019
ms.custom: seodec18, SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 9750A3F3-89C7-4A8F-BA75-B0B06BD772C2
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: ae91cc1982fa41022981c940df5436c5ea5e8e5b
ms.sourcegitcommit: 8efe6b45d65f9db23f5575c15155fe363fa12cdb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92750181"
---
# <a name="install-certificates-required-for-visual-studio-offline-installation"></a>Visual Studio çevrimdışı yükleme için gerekli sertifikaları yükleme

Çoğu bileşen düzenli olarak güncelleştirildiğinden, Visual Studio birincil olarak internet 'e bağlı bir makineye yüklenmek üzere tasarlanmıştır. Ancak, bazı ek adımlarla Visual Studio 'Yu çalışan bir internet bağlantısının kullanılamadığı bir ortamda dağıtmak mümkündür.

Visual Studio Kurulum altyapısı yalnızca güvenilen içeriği kurar. İndirilmekte olan içeriğin Authenticode imzalarını denetleyerek ve tüm içeriğe yüklemeden önce güvenildiğini doğrulayarak bunu yapar. Bu, indirme konumunun tehlikeye girdiği saldırılara karşı ortamınızı güvende tutar. Bu nedenle Visual Studio Kurulumu, bir kullanıcının makinesinde birkaç standart Microsoft Root ve ara sertifikaların yüklü ve güncel olmasını gerektirir. Makine Windows Update ile güncel tutuluyorsa imzalama sertifikaları genellikle güncel olur. Makine internet 'e bağlıysa, yükleme sırasında Visual Studio, dosya imzalarını doğrulamak için gerektiğinde sertifikaları yenileyebilir. Makine çevrimdışıysa, sertifikaların başka bir şekilde yenilenmesi gerekir.

## <a name="how-to-refresh-certificates-when-offline"></a>Çevrimdışıyken sertifikaları yenileme

Sertifikaları çevrimdışı bir ortamda yüklemek veya güncelleştirmek için üç seçenek vardır.

### <a name="option-1---manually-install-certificates-from-a-layout-folder"></a>Seçenek 1-bir düzen klasöründen sertifikaları el Ile yükler

::: moniker range="vs-2017"

Bir ağ düzeni oluşturduğunuzda, gerekli sertifikalar Sertifikalar klasörüne indirilir. Ardından sertifika dosyalarının her birine çift tıklayarak ve ardından Sertifika Yöneticisi Sihirbazı ' na tıklayarak sertifikaları el ile yükleyebilirsiniz. Parola sorulursa boş bırakın.

**Güncelleştirme** : Visual Studio 2017 sürüm 15,8 Preview 2 veya üzeri için, sertifika dosyalarının her birine sağ tıklayıp sertifikayı Güncelleştir ' i seçerek ve ardından Sertifika Yöneticisi Sihirbazı ' na tıklayarak sertifikaları el ile yükleyebilirsiniz.

::: moniker-end

::: moniker range="vs-2019"

Bir ağ düzeni oluşturduğunuzda, gerekli sertifikalar Sertifikalar klasörüne indirilir. Sertifika dosyalarının her birine sağ tıklayıp sertifikayı yükler ' i seçip Sertifika Yöneticisi Sihirbazı ' na tıklayarak sertifikaları el ile yükleyebilirsiniz. Parola sorulursa boş bırakın.

::: moniker-end

### <a name="option-2---distribute-trusted-root-certificates-in-an-enterprise-environment"></a>Seçenek 2-güvenilen kök sertifikaları kurumsal bir ortamda dağıtma

En son kök sertifikalara sahip olmayan çevrimdışı makinelere sahip kuruluşlar için yönetici, [Güvenilen kökleri ve Izin verilmeyen sertifikaları yapılandırma](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn265983(v=ws.11)) sayfasındaki yönergeleri kullanarak bunları güncelleştirebilir.

### <a name="option-3---install-certificates-as-part-of-a-scripted-deployment-of-visual-studio"></a>Seçenek 3-sertifikaları, Visual Studio 'nun betikleştirilmiş dağıtımının bir parçası olarak yükler

Visual Studio 'nun bir çevrimdışı ortamda istemci iş istasyonlarına dağıtımını yaparken bu adımları izlemeniz gerekir:

::: moniker range="vs-2017"

1. [Sertifika Yöneticisi aracını](/dotnet/framework/tools/certmgr-exe-certificate-manager-tool) (certmgr.exe) yükleme paylaşımında (örneğin, \\ server\share\vs2017) kopyalayın. Certmgr.exe, Windows 'un bir parçası olarak dahil değildir, ancak [Windows SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk)bir parçası olarak kullanılabilir.

2. Aşağıdaki komutlarla bir toplu işlem dosyası oluşturun:

   ```cmd
   certmgr.exe -add -c certificates\manifestSignCertificates.p12 -n "Microsoft Code Signing PCA 2011" -s -r LocalMachine CA

   certmgr.exe -add -c certificates\manifestSignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root

   certmgr.exe -add -c certificates\manifestCounterSignCertificates.p12 -n "Microsoft Time-Stamp PCA 2010" -s -r LocalMachine CA

   certmgr.exe -add -c certificates\manifestCounterSignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root

   certmgr.exe -add -c certificates\vs_installer_opc.SignCertificates.p12 -n "Microsoft Code Signing PCA" -s -r LocalMachine CA

   certmgr.exe -add -c certificates\vs_installer_opc.SignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root
   ```

   **Güncelleştirme** : Visual Studio 2017 sürüm 15,8 Preview 2 veya üzeri için, toplu iş dosyasını aşağıdaki komutlarla oluşturun:

   ```cmd
   certmgr.exe -add [layout path]\certificates\manifestRootCertificate.cer -n "Microsoft Root Certificate Authority 2011" -s -r LocalMachine root

   certmgr.exe -add [layout path]\certificates\manifestCounterSignRootCertificate.cer -n "Microsoft Root Certificate Authority 2010" -s -r LocalMachine root

   certmgr.exe -add [layout path]\certificates\vs_installer_opc.RootCertificate.cer -n "Microsoft Root Certificate Authority" -s -r LocalMachine root
   ```
   
   Alternatif olarak, aşağıdaki komutlarla, Windows ile birlikte gelen certutil.exe kullanan bir toplu işlem dosyası oluşturun:
   
      ```cmd
   certutil.exe -addstore -f "Root" "[layout path]\certificates\manifestRootCertificate.cer"

   certutil.exe -addstore -f "Root" "[layout path]\certificates\manifestCounterSignRootCertificate.cer"

   certutil.exe -addstore -f "Root" "[layout path]\certificates\vs_installer_opc.RootCertificate.cer"
   ```

3. Toplu iş dosyasını istemcisine dağıtın. Bu komut yükseltilmiş bir işlemden çalıştırılmalıdır.

::: moniker-end

::: moniker range="vs-2019"

1. [Sertifika Yöneticisi aracını](/dotnet/framework/tools/certmgr-exe-certificate-manager-tool) (certmgr.exe) yükleme paylaşımında (örneğin, \\ server\share\vs2019) kopyalayın. Certmgr.exe, Windows 'un bir parçası olarak dahil değildir, ancak [Windows SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk)bir parçası olarak kullanılabilir.

2. Aşağıdaki komutlarla bir toplu işlem dosyası oluşturun:

   ```cmd
   certmgr.exe -add [layout path]\certificates\manifestRootCertificate.cer -n "Microsoft Root Certificate Authority 2011" -s -r LocalMachine root

   certmgr.exe -add [layout path]\certificates\manifestCounterSignRootCertificate.cer -n "Microsoft Root Certificate Authority 2010" -s -r LocalMachine root

   certmgr.exe -add [layout path]\certificates\vs_installer_opc.RootCertificate.cer -n "Microsoft Root Certificate Authority" -s -r LocalMachine root
   ```
   
   Alternatif olarak, aşağıdaki komutlarla, Windows ile birlikte gelen certutil.exe kullanan bir toplu işlem dosyası oluşturun:
   
      ```cmd
   certutil.exe -addstore -f "Root" "[layout path]\certificates\manifestRootCertificate.cer"

   certutil.exe -addstore -f "Root" "[layout path]\certificates\manifestCounterSignRootCertificate.cer"

   certutil.exe -addstore -f "Root" "[layout path]\certificates\vs_installer_opc.RootCertificate.cer"
   ```

3. Toplu iş dosyasını istemcisine dağıtın. Bu komut yükseltilmiş bir işlemden çalıştırılmalıdır.

::: moniker-end

## <a name="what-are-the-certificates-files-in-the-certificates-folder"></a>Sertifikalar klasöründeki sertifika dosyaları nelerdir?

::: moniker range="vs-2017"

Üç. Bu klasördeki P12 dosyaları her biri bir ara sertifika ve bir kök sertifika içerir. Windows Update geçerli olan çoğu sistemde bu sertifikalar zaten yüklüdür.

* **Manifestsigncertificates. p12** şunları içerir:
  * Ara sertifika: **Microsoft kod IMZALAMA PCA 2011**
    * Gerekli değildir. Varsa, bazı senaryolarda performansı geliştirir.
  * Kök sertifika: **Microsoft kök sertifika yetkilisi 2011**
    * En son Windows güncelleştirmeleri yüklü olmayan Windows 7 Service Pack 1 sistemlerinde gereklidir.
* **Manifestcountersigncertificates. p12** şunları içerir:
  * Ara sertifika: **Microsoft Time-Stamp PCA 2010**
    * Gerekli değildir. Varsa, bazı senaryolarda performansı geliştirir.
  * Kök sertifika: **Microsoft kök sertifika yetkilisi 2010**
    * En son Windows güncelleştirmeleri yüklü olmayan Windows 7 Service Pack 1 sistemleri için gereklidir.
* **Vs_installer_opc. SignCertificates. p12** şunları içerir:
  * Ara sertifika: **Microsoft kod IMZALAMA PCA**
    * Tüm sistemler için gereklidir. Windows Update uygulanmış olan sistemlerin bu sertifikaya sahip olabileceğini unutmayın.
  * Kök sertifika: **Microsoft kök sertifika yetkilisi**
    * Gereklidir. Bu sertifika, Windows 7 veya üzerini çalıştıran sistemlerle birlikte gönderilir.

**Güncelleştirme** : Visual Studio 2017 sürüm 15,8 Preview 2 veya üzeri için, Visual Studio yükleyicisi yalnızca kök sertifikaların sisteme yüklenmesini gerektirir. Bu sertifikalar. p12 yerine. cer dosyalarında depolanır.

::: moniker-end

::: moniker range="vs-2019"

* **Manifestsigncertificates. cer** şunları içerir:
  * Kök sertifika: **Microsoft kök sertifika yetkilisi 2011**
    * En son Windows güncelleştirmeleri yüklü olmayan Windows 7 Service Pack 1 sistemlerinde gereklidir.
* **Manifestcountersigncertificates. cer** şunları içerir:
  * Kök sertifika: **Microsoft kök sertifika yetkilisi 2010**
    * En son Windows güncelleştirmeleri yüklü olmayan Windows 7 Service Pack 1 sistemleri için gereklidir.
* **Vs_installer_opc. SignCertificates. cer** şunları içerir:
  * Kök sertifika: **Microsoft kök sertifika yetkilisi**
    * Gereklidir. Bu sertifika, Windows 7 veya üzerini çalıştıran sistemlerle birlikte gönderilir.

Visual Studio Yükleyicisi, sisteme yalnızca kök sertifikaların yüklenmesini gerektirir.

::: moniker-end

## <a name="why-are-the-certificates-from-the-certificates-folder-not-installed-automatically"></a>Sertifikalar klasöründeki sertifikalar neden otomatik olarak yüklenmedi?

Bir çevrimiçi ortamda imza doğrulandığında, Windows API 'Leri, sertifikaları indirip sisteme eklemek için kullanılır. Bu işlem sırasında, sertifikaya güvenildiğini ve yönetim ayarları aracılığıyla izin verileceğini doğrulamaya yönelik doğrulama yapılır. Bu doğrulama işlemi, çoğu çevrimdışı ortamda gerçekleşemez. Sertifikaları el ile yüklemek, Kurumsal yöneticilerin sertifikaların güvenilir olmasını ve kuruluşlarındaki güvenlik ilkesini karşılamasını sağlar.

## <a name="checking-if-certificates-are-already-installed"></a>Sertifikaların zaten yüklü olup olmadığı denetleniyor

Yükleme sistemini denetetmenin bir yolu şu adımları izlemelidir:

1. **mmc.exe** çalıştırın.<br/>
  a. **Dosya** ' ya ve sonra **ek bileşen Ekle/Kaldır** ' ı seçin.<br/>
  b. **Sertifikalar** ' a çift tıklayın, **bilgisayar hesabı** ' nı seçin ve ardından **İleri** ' ye tıklayın.<br/>
  c. **Yerel bilgisayar** ' ı seçin, **son** ' a ve ardından **Tamam** ' a tıklayın.<br/>
  d. **Sertifikalar (yerel bilgisayar)** ' ı genişletin.<br/>
  e. **Güvenilen kök sertifika yetkilileri** ' ni genişletin ve ardından **Sertifikalar** ' ı seçin.<br/>
    * Gerekli kök sertifikaları için bu listeyi işaretleyin.<br/>

   f. **Ara sertifika yetkililerini** genişlettikten sonra **Sertifikalar** ' ı seçin.<br/>
    * Gerekli ara sertifikalar için bu listeyi işaretleyin.<br/>

2. **Dosya** ' ya ve sonra **ek bileşen Ekle/Kaldır** ' ı seçin.<br/>
  a. **Sertifikalar** ' a çift tıklayın, **Kullanıcı hesabım** ' ı seçin, **son** ' a ve ardından **Tamam** ' a tıklayın.<br/>
  b. **Sertifikalar – Geçerli Kullanıcı** ' yı genişletin.<br/>
  c. **Ara sertifika yetkililerini** genişlettikten sonra **Sertifikalar** ' ı seçin.<br/>
    * Gerekli ara sertifikalar için bu listeyi işaretleyin.<br/>

Sertifika adları **verilen** sütunlarda değilse, bunların yüklenmesi gerekir.  Ara sertifika yalnızca **Geçerli Kullanıcı** ara sertifika deposunda ise, yalnızca oturum açan kullanıcı tarafından kullanılabilir. Diğer kullanıcılar için yüklemeniz gerekebilir.

## <a name="install-visual-studio"></a>Visual Studio'yu yükleme

Sertifikaları yükledikten sonra, Visual Studio 'nun dağıtımı, "Visual Studio 'nun ağ yüklemesi oluşturma" sayfasının [bir ağ yüklemesinden dağıtma](create-a-network-installation-of-visual-studio.md#deploy-from-a-network-installation) bölümünden yönergeleri kullanarak devam edebilir.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio'yu yükleme](install-visual-studio.md)
* [Visual Studio yönetici kılavuzu](visual-studio-administrator-guide.md)
* [Komut satırı parametrelerini kullanarak Visual Studio'yu yükleme](use-command-line-parameters-to-install-visual-studio.md)
* [Visual Studio iş yükü ve bileşen kimlikleri](workload-and-component-ids.md)
