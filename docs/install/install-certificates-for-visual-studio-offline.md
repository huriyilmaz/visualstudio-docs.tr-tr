---
title: Çevrimdışı yükleme için gerekli sertifikaları yükleme
description: Visual Studio çevrimdışı yükleme için sertifikaları nasıl yükleyin öğrenin.
ms.date: 08/08/2019
ms.custom: seodec18
ms.topic: conceptual
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
ms.openlocfilehash: b2570876ddaa03753b1c0d3fb9f9ddc772bbbcb8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114666"
---
# <a name="install-certificates-required-for-visual-studio-offline-installation"></a>Visual Studio çevrimdışı yüklemesi için gerekli sertifikaları yükleme

Visual Studio öncelikle internete bağlı bir makineye kurulacak şekilde tasarlanmıştır, çünkü birçok bileşen düzenli olarak güncellenir. Ancak, bazı ek adımlarla Visual Studio'yı çalışan bir internet bağlantısının kullanılamadığı bir ortamda dağıtmak mümkündür.

Visual Studio kurulum motoru yalnızca güvenilen içeriği yükler. Bunu, indirilen içeriğin Authenticode imzalarını denetleyerek ve yüklemeden önce tüm içeriğin güvenilir olduğunu doğrulayarak yapar. Bu, karşıdan yükleme konumunun tehlikeye düştüğü saldırılara karşı ortamınızı korur. Visual Studio kurulumu bu nedenle, kullanıcının makinesinde birkaç standart Microsoft kök ve ara sertifikanın yüklenmesini ve güncel olmasını gerektirir. Makine Windows Update ile güncel tutulmuşsa, sertifikaları imzalama genellikle günceldir. Makine internete bağlıysa, yükleme sırasında Visual Studio dosya imzalarını doğrulamak için gerekli sertifikaları yenileyebilir. Makine çevrimdışıysa, sertifikaların başka bir şekilde yenilenmesi gerekir.

## <a name="how-to-refresh-certificates-when-offline"></a>Çevrimdışıyken sertifikaları yenileme

Sertifikaları çevrimdışı bir ortamda yüklemek veya güncelleştirmek için üç seçenek vardır.

### <a name="option-1---manually-install-certificates-from-a-layout-folder"></a>Seçenek 1 - Sertifikaları bir düzen klasöründen el ile yükleme

::: moniker range="vs-2017"

Bir ağ düzeni oluşturduğunuzda, gerekli sertifikalar Sertifikalar klasörüne indirilir. Daha sonra, sertifika dosyalarının her birini çift tıklatarak ve ardından Sertifika Yöneticisi sihirbazını tıklatarak sertifikaları el ile yükleyebilirsiniz. Parola istenirse, parolayı boş bırakın.

**Güncelleme**: Visual Studio 2017 sürüm 15.8 Önizleme 2 veya sonraki sürümiçin, sertifika dosyalarının her birine sağ tıklayarak, Sertifika Yı seçerek ve ardından Sertifika Yöneticisi sihirbazı aracılığıyla tıklayarak sertifikaları el ile yükleyebilirsiniz.

::: moniker-end

::: moniker range="vs-2019"

Bir ağ düzeni oluşturduğunuzda, gerekli sertifikalar Sertifikalar klasörüne indirilir. Sertifika dosyalarının her birine sağ tıklayarak, Sertifika Yükle'yi seçerek ve ardından Sertifika Yöneticisi sihirbazını tıklatarak sertifikaları el ile yükleyebilirsiniz. Parola istenirse, parolayı boş bırakın.

::: moniker-end

### <a name="option-2---distribute-trusted-root-certificates-in-an-enterprise-environment"></a>Seçenek 2 - Güvenilir kök sertifikalarını kurumsal ortamda dağıtma

En son kök sertifikalarına sahip olmayan çevrimdışı makinelere sahip işletmeler için yönetici, [Güvenilir Kökleri Yapılandırve İzin verilmeyen Sertifikalar](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn265983(v=ws.11)) sayfasındaki yönergeleri bunları güncelleştirmek için kullanabilir.

### <a name="option-3---install-certificates-as-part-of-a-scripted-deployment-of-visual-studio"></a>Seçenek 3 - Visual Studio komut dosyası dağıtımının bir parçası olarak sertifikaları yükleyin

Visual Studio'nun çevrimdışı bir ortamda istemci iş istasyonlarına dağıtımını komut dosyası yla komut dosyası yla komut dosyası na göre yazıyorsanız, aşağıdaki adımları izlemeniz gerekir:

::: moniker range="vs-2017"

1. Sertifika [Yöneticisi Aracını](/dotnet/framework/tools/certmgr-exe-certificate-manager-tool) (certmgr.exe) yükleme payına \\kopyalayın (örneğin, sunucu\share\vs2017). Certmgr.exe, Windows'un kendisinin bir parçası olarak dahil değildir, ancak [Windows SDK'nın](https://developer.microsoft.com/windows/downloads/windows-10-sdk)bir parçası olarak kullanılabilir.

2. Aşağıdaki komutları içeren bir toplu iş dosyası oluşturun:

   ```cmd
   certmgr.exe -add -c certificates\manifestSignCertificates.p12 -n "Microsoft Code Signing PCA 2011" -s -r LocalMachine CA

   certmgr.exe -add -c certificates\manifestSignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root

   certmgr.exe -add -c certificates\manifestCounterSignCertificates.p12 -n "Microsoft Time-Stamp PCA 2010" -s -r LocalMachine CA

   certmgr.exe -add -c certificates\manifestCounterSignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root

   certmgr.exe -add -c certificates\vs_installer_opc.SignCertificates.p12 -n "Microsoft Code Signing PCA" -s -r LocalMachine CA

   certmgr.exe -add -c certificates\vs_installer_opc.SignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root
   ```

   **Güncelleştirme**: Visual Studio 2017 sürüm 15.8 Önizleme 2 veya sonraki sürüm için, aşağıdaki komutları içeren toplu dosyayı oluşturun:

   ```cmd
   certmgr.exe -add [layout path]\certificates\manifestRootCertificate.cer -n "Microsoft Root Certificate Authority 2011" -s -r LocalMachine root

   certmgr.exe -add [layout path]\certificates\manifestCounterSignRootCertificate.cer -n "Microsoft Root Certificate Authority 2010" -s -r LocalMachine root

   certmgr.exe -add [layout path]\certificates\vs_installer_opc.RootCertificate.cer -n "Microsoft Root Certificate Authority" -s -r LocalMachine root
   ```
   
   Alternatif olarak, aşağıdaki komutlarla Windows ile birlikte gelen certutil.exe kullanan bir toplu iş dosyası oluşturun:
   
      ```cmd
   certutil.exe -addstore -f "Root" "[layout path]\certificates\manifestRootCertificate.cer"

   certutil.exe -addstore -f "Root" "[layout path]\certificates\manifestCounterSignRootCertificate.cer"

   certutil.exe -addstore -f "Root" "[layout path]\certificates\vs_installer_opc.RootCertificate.cer"
   ```

3. Toplu iş dosyasını istemciye dağıtın. Bu komut yükseltilmiş bir işlemden çalıştırılmalıdır.

::: moniker-end

::: moniker range="vs-2019"

1. Sertifika [Yöneticisi Aracını](/dotnet/framework/tools/certmgr-exe-certificate-manager-tool) (certmgr.exe) yükleme payına \\kopyalayın (örneğin, sunucu\share\vs2019). Certmgr.exe, Windows'un kendisinin bir parçası olarak dahil değildir, ancak [Windows SDK'nın](https://developer.microsoft.com/windows/downloads/windows-10-sdk)bir parçası olarak kullanılabilir.

2. Aşağıdaki komutları içeren bir toplu iş dosyası oluşturun:

   ```cmd
   certmgr.exe -add [layout path]\certificates\manifestRootCertificate.cer -n "Microsoft Root Certificate Authority 2011" -s -r LocalMachine root

   certmgr.exe -add [layout path]\certificates\manifestCounterSignRootCertificate.cer -n "Microsoft Root Certificate Authority 2010" -s -r LocalMachine root

   certmgr.exe -add [layout path]\certificates\vs_installer_opc.RootCertificate.cer -n "Microsoft Root Certificate Authority" -s -r LocalMachine root
   ```
   
   Alternatif olarak, aşağıdaki komutlarla Windows ile birlikte gelen certutil.exe kullanan bir toplu iş dosyası oluşturun:
   
      ```cmd
   certutil.exe -addstore -f "Root" "[layout path]\certificates\manifestRootCertificate.cer

   certutil.exe -addstore -f "Root" [layout path]\certificates\manifestCounterSignRootCertificate.cer"

   certutil.exe -addstore -f "Root" "[layout path]\certificates\vs_installer_opc.RootCertificate.cer"
   ```

3. Toplu iş dosyasını istemciye dağıtın. Bu komut yükseltilmiş bir işlemden çalıştırılmalıdır.

::: moniker-end

## <a name="what-are-the-certificates-files-in-the-certificates-folder"></a>Sertifikalar klasöründeki sertifika dosyaları nelerdir?

::: moniker range="vs-2017"

Üçü. Bu klasördeki P12 dosyalarının her biri bir ara sertifika ve kök sertifika içerir. Windows Update ile geçerli olan sistemlerin çoğunda bu sertifikalar zaten yüklenmiştir.

* **ManifestSignCertificates.p12** şunları içerir:
  * Ara sertifika: **Microsoft Code Signing PCA 2011**
    * Gerek yok. Varsa, bazı senaryolarda performansı artırır.
  * Kök sertifika: **Microsoft Root Certificate Authority 2011**
    * En son Windows Güncelleştirmeleri yüklü olmayan Windows 7 Service Pack 1 sistemlerinde gereklidir.
* **ManifestCounterSignCertificates.p12** şunları içerir:
  * Ara sertifika: **Microsoft Time-Stamp PCA 2010**
    * Gerek yok. Varsa, bazı senaryolarda performansı artırır.
  * Kök sertifika: **Microsoft Root Certificate Authority 2010**
    * En son Windows Güncelleştirmeleri yüklü olmayan Windows 7 Service Pack 1 sistemleri için gereklidir.
* **Vs_installer_opc. SignCertificates.p12** şunları içerir:
  * Ara sertifika: **Microsoft Code Signing PCA**
    * Tüm sistemler için gereklidir. Windows Update'ten uygulanan tüm güncelleştirmelere sahip sistemlerin bu sertifikaya sahip olmayabilir.
  * Kök sertifika: **Microsoft Root Certificate Authority**
    * Gereklidir. Bu sertifika, Windows 7 veya daha sonra çalıştıran sistemlere sahip gemiler.

**Güncelleme**: Visual Studio 2017 sürüm 15.8 Önizleme 2 veya sonraki sürüm için Visual Studio Installer'ın sisteme yüklenmesi için yalnızca kök sertifikaları gerektirir. Bu sertifikalar .p12 yerine .cer dosyalarında depolanır.

::: moniker-end

::: moniker range="vs-2019"

* **ManifestSignCertificates.cer** şunları içerir:
  * Kök sertifika: **Microsoft Root Certificate Authority 2011**
    * En son Windows Güncelleştirmeleri yüklü olmayan Windows 7 Service Pack 1 sistemlerinde gereklidir.
* **ManifestCounterSignCertificates.cer** içerir:
  * Kök sertifika: **Microsoft Root Certificate Authority 2010**
    * En son Windows Güncelleştirmeleri yüklü olmayan Windows 7 Service Pack 1 sistemleri için gereklidir.
* **Vs_installer_opc. SignCertificates.cer** şunları içerir:
  * Kök sertifika: **Microsoft Root Certificate Authority**
    * Gereklidir. Bu sertifika, Windows 7 veya daha sonra çalıştıran sistemlere sahip gemiler.

Visual Studio Yükleyici sisteme yüklenmesi için yalnızca kök sertifikaları gerektirir.

::: moniker-end

## <a name="why-are-the-certificates-from-the-certificates-folder-not-installed-automatically"></a>Sertifikalar klasöründeki sertifikalar neden otomatik olarak yüklenmiyor?

Bir imza çevrimiçi ortamda doğrulandığında, Sertifikaları indirmek ve sisteme eklemek için Windows API'leri kullanılır. Bu işlem sırasında, sertifikanın yönetim ayarları yla güvenilir ve izin verilen doğrulama gerçekleşir. Bu doğrulama işlemi çoğu çevrimdışı ortamlarda oluşamaz. Sertifikaların el ile yüklenmesi, kurumsal yöneticilerin sertifikalara güvenilmesini ve kuruluşlarının güvenlik ilkesini karşılamasını sağlar.

## <a name="checking-if-certificates-are-already-installed"></a>Sertifikaların zaten yüklü olup olmadığını denetleme

Yükleme sistemini denetlemenin bir yolu aşağıdaki adımları izlemektir:

1. **Çalıştır mmc.exe**.<br/>
  a. **Dosya'yı**tıklatın ve ardından **Ekle/Kaldır'ı**seçin.<br/>
  b. **Sertifikalar'ı**çift tıklatın, **Bilgisayar hesabını**seçin ve sonra **İleri'yi**tıklatın.<br/>
  c. **Yerel bilgisayarı**seçin, **Bitir'i**tıklatın ve ardından **Tamam'ı**tıklatın.<br/>
  d. Sertifikaları Genişlet **(Yerel Bilgisayar)**.<br/>
  e. **Güvenilen Kök Sertifika Yetkilileri'ni**genişletin ve ardından **Sertifikaları**seçin.<br/>
    * Gerekli kök sertifikalar için bu listeyi kontrol edin.<br/>

   f. **Ara Sertifika Yetkililerini**Genişletin ve **ardından Sertifikaları**seçin.<br/>
    * Gerekli ara sertifikalar için bu listeyi kontrol edin.<br/>

2. **Dosya'yı**tıklatın ve ardından **Ekle/Kaldır'ı**seçin.<br/>
  a. **Sertifikaları**çift tıklatın, **Kullanıcı hesabımı**seçin , **Bitir'i**tıklatın ve ardından **Tamam'ı**tıklatın.<br/>
  b. Sertifikaları Genişlet **– Güncel Kullanıcı**.<br/>
  c. **Ara Sertifika Yetkililerini**Genişletin ve **ardından Sertifikaları**seçin.<br/>
    * Gerekli ara sertifikalar için bu listeyi kontrol edin.<br/>

Sertifika adları **Verilen Sütunlarda** yoksa, yüklenmesi gerekir.  Bir ara sertifika yalnızca **Geçerli Kullanıcı** Ara Sertifikası deposundaysa, yalnızca oturum açan kullanıcı tarafından kullanılabilir. Diğer kullanıcılar için yüklemeniz gerekebilir.

## <a name="install-visual-studio"></a>Visual Studio yükleme

Sertifikaları yükledikten sonra Visual Studio dağıtımı, "Visual Studio'nun ağ yüklemesi oluşturma" sayfasının [ağ yükleme bölümünden Dağıtım](create-a-network-installation-of-visual-studio.md#deploy-from-a-network-installation) yönergelerini kullanarak devam edebilir.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio yükleme](install-visual-studio.md)
* [Visual Studio yönetici kılavuzu](visual-studio-administrator-guide.md)
* [Visual Studio'yı yüklemek için komut satırı parametrelerini kullanma](use-command-line-parameters-to-install-visual-studio.md)
* [Visual Studio iş yükü ve bileşen kimlikleri](workload-and-component-ids.md)
