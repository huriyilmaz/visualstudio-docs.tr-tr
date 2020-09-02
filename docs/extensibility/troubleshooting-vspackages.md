---
title: VSPackages sorunlarını giderme | Microsoft Docs
ms.date: 11/04/2016
ms.topic: troubleshooting
helpviewer_keywords:
- VSPackages, troubleshooting
- debugging, VSPackages
ms.assetid: 274673e7-72e7-476f-a263-3411b5b874be
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f79bfcb73749992365b167bae84a15de17d2440d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "87235036"
---
# <a name="troubleshooting-vspackages"></a>VSPackage Sorunlarını Giderme
Bu sorunları çözmek için VSPackage ve ipuçlarınız ile sahip olabileceğiniz yaygın sorunlar aşağıda verilmiştir.

### <a name="to-troubleshoot-a-vspackage-that-keeps-visual-studio-from-starting"></a>Visual Studio 'Nun başlamasını engelleyen bir VSPackage sorunlarını gidermek için

- [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Güvenli modda başlatın.

   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Güvenli modda başlamak için, bir komut isteminde **devenv.exe/safemode**yazın.

   Bu işlem sırasında, ile birlikte gelen VSPackages 'lar hariç hiçbir VSPackages yüklenmez [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

### <a name="to-troubleshoot-a-vspackage-that-does-not-load"></a>Yüklenmeyen bir VSPackage sorunlarını gidermek için

1. VSPackage 'ın çalıştırmak için kaydedildiği kayıt defteri kökünü, genellikle Deneysel kayıt defteri kökünü kullandığınızdan emin olun.

    Daha fazla bilgi için bkz. [deneysel örnek](../extensibility/the-experimental-instance.md).

2. VSPackage, Deneysel kayıt defteri kökünde çalışmayı hedeflediyse, Deneysel sürümünü çalıştırdığınızdan emin olun [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

    Deneysel sürümü çalıştırmak için, komut penceresine şunu yazın: **devenv/rootsuffix exp**.

3. VSPackage kayıt defteri girdilerinizi denetleyin.

    Daha fazla bilgi için bkz. [VSPackages 'Yi kaydetme](registering-and-unregistering-vspackages.md) ve [VSPackages 'i yönetme](../extensibility/managing-vspackages.md).

4. **Output** [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSPackage yüklemesi başarısız olan örneğinin çıkış penceresini açın. VSPackage 'ın neden yükleme başarısız olduğuna ilişkin bilgiler bu pencerede görüntülenebilir.

   > [!NOTE]
   > ' In Deneysel sürümünü [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Tümleşik geliştirme ORTAMıNDAN (IDE) başlatıyorsanız, her iki sürümün de **Çıkış** penceresini inceleyin.

5. Etkinlik günlüğünü inceleyin.

    Daha fazla bilgi için bkz. [nasıl yapılır: etkinlik günlüğünü kullanma](../extensibility/how-to-use-the-activity-log.md).

6. IDE tarafından oluşturulan özel durumlar hakkında daha fazla bilgi için, özel durumları etkinleştirmek üzere **hata ayıklama** menüsündeki **özel durumlar** ' a tıklayın. **Özel durumlar** iletişim kutusunda daha fazla bilgi edinmek istediğiniz özel durum türlerini seçin.

### <a name="to-troubleshoot-a-vspackage-that-does-not-register"></a>Kaydolmayan bir VSPackage sorunlarını gidermek için

1. VSPackage derlemesinin güvenilir bir konumda bulunduğundan emin olun. RegPkg, derlemeleri varsayılan .NET güvenlik yapılandırmasındaki ağ paylaşma gibi güvenilmeyen veya kısmen güvenilen bir konuma kaydedemez. Bir Kullanıcı güvenilmeyen bir konumda bir proje oluşturduğunda bir uyarı görünse de, "Bu iletiyi bir daha gösterme" onay kutusu bu uyarının yeniden oluşmasını engelleyebilir.

### <a name="to-troubleshoot-a-command-that-is-not-visible-or-that-generates-an-error-when-you-click-a-command"></a>Görünür olmayan veya bir komuta tıkladığınızda hata üreten bir komutun sorunlarını gidermek için

1. Komut Istemine aşağıdaki komutu yazarak yeni veya değiştirilmiş menü komutlarını ve IDE 'de zaten var olanları birleştirin [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] : **devenv/rootsuffix exp/Setup**.

2. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]VSPackage için UI.dll bulabileceğinizi doğrulayın.

   1. Kayıt defterinin paketler bölümünde VSPackage 'un CLSID 'sini bulun:

        HKLM\Software\Microsoft\Visual Studio \\ *\<version>* \packages

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

        Yönetilen kod için, başarısız derleme yüklerinin ayrıntılarını göstermek üzere [Fuslogvw.exe (derleme bağlama günlük Görüntüleyicisi)](/dotnet/framework/tools/fuslogvw-exe-assembly-binding-log-viewer) kullanabilirsiniz.

2. Yönetilmeyen kod için, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] CLSID kayıt defteri düğümünde VSPackage CLSID 'sini bulun:

    HKLM\Software\Microsoft\Visual Studio \\ *\<version>* \CLSID

   Inprocserver32 girişinin VSPackage dll dosyasının doğru yoluna sahip olduğundan emin olun.

## <a name="see-also"></a>Ayrıca bkz.
- [VSPackage’lar](../extensibility/internals/vspackages.md)
- [Visual Studio sorunlarını giderme](/troubleshoot/visualstudio/welcome-visual-studio/)
