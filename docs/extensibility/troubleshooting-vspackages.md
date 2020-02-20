---
title: VSPackages sorunlarını giderme | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, troubleshooting
- debugging, VSPackages
ms.assetid: 274673e7-72e7-476f-a263-3411b5b874be
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a231d8d02ce7432188053293684d09c7243dfd5e
ms.sourcegitcommit: 260d093d2287ba791f28bdc7103493beabf80b2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77506405"
---
# <a name="troubleshooting-vspackages"></a>VSPackage Sorunlarını Giderme
Bu sorunları çözmek için VSPackage ve ipuçlarınız ile sahip olabileceğiniz yaygın sorunlar aşağıda verilmiştir.

### <a name="to-troubleshoot-a-vspackage-that-keeps-visual-studio-from-starting"></a>Visual Studio 'Nun başlamasını engelleyen bir VSPackage sorunlarını gidermek için

- Güvenli modda [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] başlatın.

   Güvenli modda [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] başlatmak için komut isteminde **devenv. exe/safemode**yazın.

   Bu işlem sırasında, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]eklenen VSPackages dışında VSPackages yüklenmez.

### <a name="to-troubleshoot-a-vspackage-that-does-not-load"></a>Yüklenmeyen bir VSPackage sorunlarını gidermek için

1. VSPackage 'ın çalıştırmak için kaydedildiği kayıt defteri kökünü, genellikle Deneysel kayıt defteri kökünü kullandığınızdan emin olun.

    Daha fazla bilgi için bkz. [deneysel örnek](../extensibility/the-experimental-instance.md).

2. VSPackage, Deneysel kayıt defteri kökünde çalışmayı hedeflediyse, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Deneysel sürümünü çalıştırdığınızdan emin olun.

    Deneysel sürümü çalıştırmak için, komut penceresine şunu yazın: **devenv/rootsuffix exp**.

3. VSPackage kayıt defteri girdilerinizi denetleyin.

    Daha fazla bilgi için bkz. [VSPackages 'Yi kaydetme](registering-and-unregistering-vspackages.md) ve [VSPackages 'i yönetme](../extensibility/managing-vspackages.md).

4. VSPackage yüklemesi başarısız olan [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] örneğinin **Çıkış** penceresini açın. VSPackage 'ın neden yükleme başarısız olduğuna ilişkin bilgiler bu pencerede görüntülenebilir.

   > [!NOTE]
   > [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] tümleşik geliştirme ortamından (IDE) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Deneysel sürümünü başlatıyorsanız her iki sürümün de **Çıkış** penceresini inceleyin.

5. Etkinlik günlüğünü inceleyin.

    Daha fazla bilgi için bkz. [nasıl yapılır: etkinlik günlüğünü kullanma](../extensibility/how-to-use-the-activity-log.md).

6. IDE tarafından oluşturulan özel durumlar hakkında daha fazla bilgi için, özel durumları etkinleştirmek üzere **hata ayıklama** menüsündeki **özel durumlar** ' a tıklayın. **Özel durumlar** iletişim kutusunda daha fazla bilgi edinmek istediğiniz özel durum türlerini seçin.

### <a name="to-troubleshoot-a-vspackage-that-does-not-register"></a>Kaydolmayan bir VSPackage sorunlarını gidermek için

1. VSPackage derlemesinin güvenilir bir konumda bulunduğundan emin olun. RegPkg, derlemeleri varsayılan .NET güvenlik yapılandırmasındaki ağ paylaşma gibi güvenilmeyen veya kısmen güvenilen bir konuma kaydedemez. Bir Kullanıcı güvenilmeyen bir konumda bir proje oluşturduğunda bir uyarı görünse de, "Bu iletiyi bir daha gösterme" onay kutusu bu uyarının yeniden oluşmasını engelleyebilir.

### <a name="to-troubleshoot-a-command-that-is-not-visible-or-that-generates-an-error-when-you-click-a-command"></a>Görünür olmayan veya bir komuta tıkladığınızda hata üreten bir komutun sorunlarını gidermek için

1. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] komut Istemine aşağıdakini yazarak yeni veya değiştirilmiş menü komutlarını ve IDE 'de zaten mevcut olanları birleştirin: **devenv/rootsuffix exp/Setup**.

2. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], VSPackage için UI. dll ' nin bulabileceği emin olun.

   1. Kayıt defterinin paketler bölümünde VSPackage 'un CLSID 'sini bulun:

        HKLM\Software\Microsoft\Visual Studio\\ *\<sürümü >* \packages

   2. SatelliteDll alt anahtarı tarafından verilen yolun doğru olduğundan emin olun.

### <a name="to-troubleshoot-a-vspackage-that-behaves-unexpectedly"></a>Beklenmedik şekilde davranan bir VSPackage sorunlarını gidermek için

1. Kodunuzda kesme noktaları ayarlayın.

     Hata ayıklama için iyi başlangıç noktaları, Oluşturucu ve başlatma yöntemidir. Ayrıca, bir menü komutu gibi değerlendirmek istediğiniz alanda kesme noktaları da ayarlayabilirsiniz. Kesme noktalarını etkinleştirmek için hata ayıklayıcı altında çalıştırmanız gerekir.

    1. **Proje** menüsünde **Özellikler**' e tıklayın.

    2. **Özellik sayfaları** Iletişim kutusunda **Hata Ayıkla** sekmesini seçin.

    3. **Komut satırı bağımsız değişkenleri** kutusunda, VSPackage hedeflediği geliştirme ortamının kök sonekini yazın. Örneğin, deneysel derlemeyi seçmek için şunu yazın: **/rootsuffix exp**.

    4. **Hata Ayıkla** menüsünde, **hata ayıklamayı Başlat** ' a tıklayın veya F5 tuşuna basın.

        > [!NOTE]
        > Bir projede hata ayıklaması yapıyorsanız, şimdi projenizin mevcut bir örneğini oluşturun veya yükleyin.

2. Etkinlik günlüğünü kullanın.

     Anahtar noktalarında etkinlik günlüğüne bilgi yazarak VSPackage davranışını izleyin. Bu teknik, özellikle bir perakende ortamında VSPackage çalıştırdığınızda yararlı olur. Daha fazla bilgi için bkz. [nasıl yapılır: etkinlik günlüğünü kullanma](../extensibility/how-to-use-the-activity-log.md).

3. Ortak sembolleri kullanın.

     Hata ayıklama sırasında okunabilirliği artırmak için, hata ayıklayıcıya semboller ekleyebilirsiniz.

    1. **Araçlar/Seçenekler** menüsünden **hata ayıklama/Semboller** iletişim kutusuna gidin.

    2. Bu **sembol dosyası (. pdb) konumunu**ekleyin:

         `https://msdl.microsoft.com/download/symbols`

    3. Performansı artırmak için, bir sembol önbellek klasörü belirtin, örneğin:

        ```
        C:\symbols
        ```

### <a name="to-troubleshoot-a-missing-vspackage-or-one-of-its-dependencies"></a>Eksik bir VSPackage veya bağımlılıklarından biri sorunlarını gidermek için

1. Yönetilen kod için başvuru yollarının doğru olduğundan emin olun.

   1. **Proje** menüsünde **Özellikler**' e tıklayın.

   2. **Özellik sayfaları** Iletişim kutusundaki **Başvurular** sekmesini seçin ve tüm yolların doğru olduğundan emin olun. Alternatif olarak, başvurulan nesnelere gitmek için **nesne tarayıcısı** kullanabilirsiniz.

        Yönetilen kod için, başarısız derleme yüklerinin ayrıntılarını göstermek üzere [Fuslogvw. exe ' yi (derleme bağlama günlük Görüntüleyicisi)](/dotnet/framework/tools/fuslogvw-exe-assembly-binding-log-viewer) kullanabilirsiniz.

2. Yönetilmeyen kod için [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] CLSID kayıt defteri düğümünde VSPackage CLSID 'sini bulun:

    HKLM\Software\Microsoft\Visual Studio\\ *\<sürümü >* \CLSID

   Inprocserver32 girişinin VSPackage dll dosyasının doğru yoluna sahip olduğundan emin olun.

## <a name="see-also"></a>Ayrıca bkz.
- [VSPackage’lar](../extensibility/internals/vspackages.md)