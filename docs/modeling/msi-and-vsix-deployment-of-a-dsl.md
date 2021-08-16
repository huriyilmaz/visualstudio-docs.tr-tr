---
title: DSL'nin MSI ve VSIX Dağıtımı
description: Kendi bilgisayarınıza veya diğer bilgisayarlara bir etki alanına özgü dili (DSL) nasıl yükleyebileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 3311e660d3d485c2a75aa1134e5c31516e39873c62fd8c05d90cdbd61169d133
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121411015"
---
# <a name="msi-and-vsix-deployment-of-a-dsl"></a>DSL'nin MSI ve VSIX Dağıtımı
Kendi bilgisayarınıza veya diğer bilgisayarlara, etki alanına özgü bir dil yükleyebilirsiniz. Visual Studio hedef bilgisayara zaten yüklenmiş olmalıdır.

## <a name="choosing-between-vsix-and-msi-deployment"></a><a name="which"></a> VSıX ve MSI dağıtımı arasında seçim yapma
 Etki alanına özgü dil dağıtmanın iki yöntemi vardır:

|Yöntem|Avantajlar|
|-|-|
|vsx (Visual Studio uzantısı)|Dağıtım çok kolay: **. vsix** dosyasını DslPackage projesinden kopyalayın ve yürütün.<br /><br /> Daha fazla bilgi için bkz. [VSX kullanarak DSL yükleme ve kaldırma](#Installing).|
|MSI (yükleyici dosyası)|-kullanıcının bir DSL dosyasına çift tıklayarak Visual Studio açmasına izin verir.<br />-Bir simgeyi hedef bilgisayardaki DSL dosyası türüyle ilişkilendirir.<br />-Bir XSD (XML Şeması) DSL dosya türüyle ilişkilendirir. Bu, dosya Visual Studio yüklendiğinde uyarıları önler.<br /><br /> MSI oluşturmak için çözümünüze bir kurulum projesi eklemeniz gerekir.<br /><br /> Daha fazla bilgi için bkz. [MSI dosyası kullanarak DSL dağıtma](#msi).|

## <a name="install-and-uninstall-a-dsl-by-using-the-vsx"></a><a name="Installing"></a> VSX kullanarak DSL yükleme ve kaldırma

bu yöntem tarafından dsl yüklendiğinde, kullanıcı Visual Studio içinden bir DSL dosyası açabilir, ancak dosya Windows gezgini ' nden açılamaz.

### <a name="to-install-a-dsl-by-using-the-vsx"></a>VSX kullanarak bir DSL yüklemek için

1. DSL paketi projeniz tarafından oluşturulan **. vsix** dosyasını bulun:

   1. **Çözüm Gezgini**, **DslPackage** projesine sağ tıklayın ve ardından **Dosya Gezgini 'nde klasörü aç**' a tıklayın.

   2. Dosya **\\ \* bin \\**_projesini_ bulun **. DslPackage. vsix**

2. **. Vsix** dosyasını, DSL 'yi yüklemek istediğiniz hedef bilgisayara kopyalayın. Bu, kendi bilgisayarınız veya başka bir tane olabilir.

   - Hedef bilgisayarda, [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] çalışma zamanında DSLs 'yi destekleyen sürümlerinden biri olmalıdır. daha fazla bilgi için bkz. [görselleştirme için desteklenen Visual Studio sürümleri & modelleme SDK](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md).

   - hedef bilgisayar, **DslPackage\source.extensions.manifest** içinde belirtilen Visual Studio sürümlerinden birine sahip olmalıdır.

3. Hedef bilgisayarda **. vsix** dosyasına çift tıklayın.

    **Visual Studio uzantısı yükleyicisi** açılır ve uzantıyı yüklüyor.

4. Başlatın veya yeniden başlatın [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] .

5. dsl 'yi test etmek için Visual Studio kullanarak dsl 'niz için tanımladığınız uzantıya sahip yeni bir dosya oluşturun.

### <a name="to-uninstall-a-dsl-that-was-installed-by-using-vsx"></a>VSX kullanılarak yüklenen bir DSL 'yi kaldırmak için

1. **Araçlar** menüsünde **Uzantılar ve güncelleştirmeler**' i seçin.

2. **Yüklü uzantıları** genişletin.

3. DSL 'nin tanımlandığı uzantıyı seçin ve ardından **Kaldır**' a tıklayın.

   Nadiren, hatalı bir uzantı yükleme başarısız olur ve hata penceresinde bir rapor oluşturur, ancak Uzantı Yöneticisi 'nde görünmez. Bu durumda, dosyayı öğesinden silerek uzantıyı kaldırabilirsiniz:

   *LocalAppData* **\Microsoft\visualstudio\10.0\Extensions**

## <a name="deploying-a-dsl-in-an-msi"></a><a name="msi"></a> MSI içinde DSL dağıtma
 dsl 'niz için bir msı (Windows Installer) dosyası tanımlayarak, kullanıcıların Windows gezgin 'den dsl dosyalarını açmasına izin verebilirsiniz. Ayrıca, dosya adı uzantınızla bir simge ve kısa açıklama ilişkilendirebilirsiniz. Buna ek olarak, MSI DSL dosyalarını doğrulamak için kullanılabilen bir XSD 'yi de yükleyebilir. İsterseniz, diğer bileşenleri MSI 'ye aynı anda yüklenecek şekilde ekleyebilirsiniz.

 MSI dosyaları ve diğer dağıtım seçenekleri hakkında daha fazla bilgi için bkz. [uygulamaları, hizmetleri ve bileşenleri dağıtma](../deployment/deploying-applications-services-and-components.md).

 bir msı oluşturmak için Visual Studio çözümünüze bir kurulum projesi eklersiniz. Bir kurulum projesi oluşturmanın en kolay yöntemi, [VMSDK sitesinden](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)indirebileceğiniz CreateMsiSetupProject.tt şablonunu kullanmaktır.

### <a name="to-deploy-a-dsl-in-an-msi"></a>MSI içinde DSL dağıtmak için

1. `InstalledByMsi`Uzantı bildiriminde ayarlanır. Bu, VSX 'in MSI dışında yüklenmesini ve kaldırılmasını engeller. Bu, MSI 'ye diğer bileşenleri dahil etmek için önemlidir.

   1. Açık DslPackage\source.extension.tt

   2. Önce aşağıdaki satırı ekleyin `<SupportedProducts>` :

       ```xml
       <InstalledByMsi>true</InstalledByMsi>
       ```

2. Windows Explorer 'da DSL 'yi temsil edecek bir simge oluşturun veya düzenleyin. Örneğin, **Dslpackage\resources\file.exe** dosyasını düzenleyin

3. DSL 'nizin aşağıdaki özniteliklerinin doğru olduğundan emin olun:

   - DSL Gezgini ' nde kök düğümüne tıklayın ve Özellikler penceresi ' de şunları gözden geçirin:

       - Açıklama

       - Sürüm

   - **Düzenleyici** düğümüne tıklayın ve Özellikler penceresi **simgesine** tıklayın. Değeri **Dslpackage\resources** içindeki **File. ico** gibi bir simge dosyasına başvuracak şekilde ayarlayın.

   - **Yapı** menüsünde **Configuration Manager** açın ve derlemek istediğiniz yapılandırmayı (örneğin, **yayın** veya **hata ayıklama**) seçin.

4. [Görselleştirme ve modelleme SDK 'sı giriş sayfasına](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)gidin ve **indirmeler** sekmesinden **CreateMsiSetupProject.tt** indirin.

5. DSL projenize **CreateMsiSetupProject.tt** ekleyin.

    Visual Studio, **createmsısetupproject. vdproj** adlı bir dosya oluşturacak.

6. Windows Explorer 'da Dsl \\ *. vdproj öğesini Setup adlı yeni bir klasöre kopyalayın.

    (İsterseniz, CreateMsiSetupProject.tt artık DSL projenizden dışarıda bırakabilirsiniz.)

7. **Çözüm Gezgini**, var olan bir proje olarak **Setup \\ \* . VDPROJ** öğesini ekleyin.

8. **Project** menüsünde **Project bağımlılıklar**' a tıklayın.

    **Project bağımlılıklar** iletişim kutusunda kurulum projesini seçin.

    **DslPackage** seçeneğinin yanındaki kutuyu seçin.

9. Çözümü yeniden derleyin.

10. Windows gezgini ' nde, kurulum projenizde oluşturulan msı dosyasını bulun.

     MSI dosyasını, DSL 'yi yüklemek istediğiniz bir bilgisayara kopyalayın. MSI dosyasına çift tıklayın. Yükleyici çalışır.

11. Hedef bilgisayarda, DSL 'niz dosya uzantısına sahip yeni bir dosya oluşturun. Şunları doğrulayın:

    - Windows gezgin liste görünümünde dosya, tanımladığınız simge ve açıklama ile birlikte görüntülenir.

    - dosyayı çift tıklattığınızda Visual Studio başlatılır ve dsl dosyasını dsl düzenleyicisinde açar.

    İsterseniz, Kurulum projesini metin şablonunu kullanmak yerine el ile oluşturabilirsiniz. Bu yordamı içeren bir anlatım için [görselleştirme ve modelleme SDK laboratuvarının](https://code.msdn.microsoft.com/DSLToolsLab/Release/ProjectReleases.aspx?ReleaseId=4207)5. bölümüne bakın.

### <a name="to-uninstall-a-dsl-that-was-installed-from-an-msi"></a>MSI 'dan yüklenmiş bir DSL 'yi kaldırmak için

1. Windows ' de, **programlar ve özellikler** denetim masasını açın.

2. DSL 'yi kaldırın.

3. Visual Studio’yu yeniden başlatın.
