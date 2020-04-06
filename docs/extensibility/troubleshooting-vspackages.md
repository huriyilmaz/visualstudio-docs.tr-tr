---
title: Sorun Giderme VSPackages | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, troubleshooting
- debugging, VSPackages
ms.assetid: 274673e7-72e7-476f-a263-3411b5b874be
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a4827a36bd8e76462a137ae7e903c1ab624121c0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698925"
---
# <a name="troubleshooting-vspackages"></a>VSPackage Sorunlarını Giderme
VSPackage'ınızla ilgili sık karşılaşılan sorunlar ve sorunları çözmek için ipuçları aşağıda verilmiştir.

### <a name="to-troubleshoot-a-vspackage-that-keeps-visual-studio-from-starting"></a>Visual Studio'nun başlamasını engelleyen bir VSPackage'ın sorunlarını gidermek için

- Güvenli [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] modda başlayın.

   Güvenli [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] modda başlamak için komut istemiyle **devenv.exe /safemode**yazın.

   Bu işlem sırasında, vspackages ile [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]birlikte vspackages dışında hiçbir VSPackages yüklenir.

### <a name="to-troubleshoot-a-vspackage-that-does-not-load"></a>Yüklenmeyen bir VSPackage sorun gidermek için

1. VSPackage'ın çalıştırmak için kayıtlı olduğu kayıt defteri kökünü(genellikle deneysel kayıt defteri kökü) kullandığınızdan emin olun.

    Daha fazla bilgi için [Deneysel Örnek'e](../extensibility/the-experimental-instance.md)bakın.

2. VSPackage deneysel kayıt defteri kökünde çalıştırmak için hedeflenmişse, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]'nin deneysel sürümünü çalıştırdığınızdan emin olun.

    Deneysel sürümü çalıştırmak için, bir komut penceresinde aşağıdaki yazın: **devenv /rootsuffix exp**.

3. VSPackage kayıt defteri girişlerinizi kontrol edin.

    Daha fazla bilgi için [vspackages kaydetme](registering-and-unregistering-vspackages.md) ve [VSPackages yönetme'ye](../extensibility/managing-vspackages.md)bakın.

4. VSPackage **Output** yüklemek için başarısız [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] olduğu örneğin Çıkış penceresini açın. VSPackage'ın neden yüklenmediğine ilişkin bilgiler bu pencerede görüntülenebilir.

   > [!NOTE]
   > Tümleşik geliştirme ortamından [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] (IDE) deneysel sürümübaşlatılıyorsanız, her iki sürümün Çıkış penceresini inceleyin. **Output** [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]

5. Etkinlik günlüğünü inceleyin.

    Daha fazla bilgi için [bkz: Etkinlik Günlüğü'nün kullanımı.](../extensibility/how-to-use-the-activity-log.md)

6. IDE tarafından atılan özel durumlar hakkında daha fazla bilgi için, özel durumları etkinleştirmek için **Hata Ayıklama** menüsünde **Özel Durumlar'ı** tıklatın. Özel **Durumlar** iletişim kutusunda, hakkında daha fazla bilgi istediğiniz özel durum türlerini seçin.

### <a name="to-troubleshoot-a-vspackage-that-does-not-register"></a>Kaydolmayan bir VSPackage sorun gidermek için

1. VSPackage derlemesinin güvenilir bir konumda bulunduğundan emin olun. RegPkg, varsayılan .net güvenlik yapılandırmasındaki ağ paylaşımı gibi güvenilmeyen veya kısmen güvenilen bir konumda derlemeleri kaydedemez. Bir kullanıcı güvenilmeyen bir konumda proje oluşturduğunda bir uyarı görünse de, "bu iletiyi bir daha gösterme" onay kutusu bu uyarının yinelemesini engelleyebilir.

### <a name="to-troubleshoot-a-command-that-is-not-visible-or-that-generates-an-error-when-you-click-a-command"></a>Görünmeyen veya bir komutu tıklattığınızda hata oluşturan bir komutu gidermek için

1. Komut Komut KomutU Komut Uğrama aşağıdakileri yazarak yeni veya değiştirilmiş menü komutları ve Zaten IDE olanlar birleştirme: **devenv /rootsuffix Exp / kurulum**. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]

2. VSPackage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] için UI.dll bulabileceğinizden emin olun.

   1. VSPackage CLSID'yi kayıt defterinin Paketler bölümünde bulun:

        HKLM\Software\Microsoft\Visual\\Studio*\<sürümü>* \Packages

   2. SatelliteDll alt anahtarı tarafından verilen yolun doğru olduğunu doğrulayın.

### <a name="to-troubleshoot-a-vspackage-that-behaves-unexpectedly"></a>Beklenmeyen bir şekilde görünen bir VSPackage sorungidermek için

1. Kodunuzda kesme noktaları ayarlayın.

     Hata ayıklama için iyi başlangıç noktaları oluşturucu ve başlatma yöntemidir. Ayrıca, menü komutu gibi değerlendirmek istediğiniz alanda kesme noktaları da ayarlayabilirsiniz. Kesme noktalarını etkinleştirmek için hata ayıklamanın altında çalışmanız gerekir.

    1. **Proje** menüsünde **Özellikler'i**tıklatın.

    2. Özellik **Sayfaları** iletişim kutusunda Hata **Ayıklama** sekmesini seçin.

    3. Komut **satırı bağımsız değişkenleri** kutusuna, VSPackage'ınızın hedefleneği geliştirme ortamının kök sonekini yazın. Örneğin, deneysel yapıyı seçmek için, yazın: **/RootSuffix Exp**.

    4. Hata **Ayıklama** menüsünde **Hata Ayıklama'yı Başlat'ı** tıklatın veya F5 tuşuna basın.

        > [!NOTE]
        > Bir projeyi hata ayıklıyorsanız, projenizin varolan bir örneğini şimdi oluşturun veya yükleyin.

2. Etkinlik günlüğünü kullanın.

     Önemli noktalardaki etkinlik günlüğüne bilgi yazarak VSPackage davranışını izle. Bu teknik, özellikle bir PERAKENDE ortamında bir VSPackage çalıştırdığınızda yararlıdır. Daha fazla bilgi için [bkz: Etkinlik Günlüğü'nün kullanımı.](../extensibility/how-to-use-the-activity-log.md)

3. Ortak semboller kullanın.

     Hata ayıklama sırasında okunabilirliği artırmak için hata ayıklayana semboller ekleyebilirsiniz.

    1. **Araçlar/Seçenekler** menüsünden **Hata Ayıklama/Semboller** iletişim kutusuna gidin.

    2. Bu **Sembol dosya (.pdb) konumu**ekle:

         `https://msdl.microsoft.com/download/symbols`

    3. Performansı artırmak için, örneğin bir simge önbellek klasörü belirtin:

        ```
        C:\symbols
        ```

### <a name="to-troubleshoot-a-missing-vspackage-or-one-of-its-dependencies"></a>Eksik bir VSPackage'ı veya bağımlılıklarından birini gidermek için

1. Yönetilen kod için başvuru yollarının doğru olduğundan emin olun.

   1. **Proje** menüsünde **Özellikler'i**tıklatın.

   2. **Özellik Sayfaları** iletişim kutusundaki **Başvurular** sekmesini seçin ve tüm yolların doğru olduğundan emin olun. Alternatif olarak, başvurulan nesnelere göz atmak için **Nesne Tarayıcısı'nı** kullanabilirsiniz.

        Yönetilen kod için, başarısız derleme yüklerinin ayrıntılarını görüntülemek için [Fuslogvw.exe 'yi (Derleme Bağlama Log Viewer)](/dotnet/framework/tools/fuslogvw-exe-assembly-binding-log-viewer) kullanabilirsiniz.

2. Yönetilmeyen kod için, CLSID kayıt düğümünde [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSPackage CLSID'yi bulun:

    HKLM\Software\Microsoft\Visual\\Studio*\<sürümü>* \CLSID

   InprocServer32 girişinin VSPackage dLL'nin doğru yolu olduğundan emin olun.

## <a name="see-also"></a>Ayrıca bkz.
- [VSPackage’lar](../extensibility/internals/vspackages.md)
