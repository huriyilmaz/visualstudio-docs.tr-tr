---
title: DSL'nin MSI ve VSIX Dağıtımı
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 96922848adf053e3b728196a445407f3d5f86428
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590195"
---
# <a name="msi-and-vsix-deployment-of-a-dsl"></a>DSL'nin MSI ve VSIX Dağıtımı
Kendi bilgisayarınıza veya diğer bilgisayarlara, etki alanına özgü bir dil yükleyebilirsiniz. Visual Studio 'Nun hedef bilgisayarda zaten yüklü olması gerekir.

## <a name="which"></a>VSıX ve MSI dağıtımı arasında seçim yapma
 Etki alanına özgü dil dağıtmanın iki yöntemi vardır:

|Yöntem|Yararları|
|-|-|
|VSX (Visual Studio uzantısı)|Dağıtım çok kolay: **. vsix** dosyasını DslPackage projesinden kopyalayın ve yürütün.<br /><br /> Daha fazla bilgi için bkz. [VSX kullanarak DSL yükleme ve kaldırma](#Installing).|
|MSI (yükleyici dosyası)|-Kullanıcının bir DSL dosyasına çift tıklayarak Visual Studio 'Yu açmasına izin verir.<br />-Bir simgeyi hedef bilgisayardaki DSL dosyası türüyle ilişkilendirir.<br />-Bir XSD (XML Şeması) DSL dosya türüyle ilişkilendirir. Bu, dosya Visual Studio 'ya yüklendiğinde uyarıları önler.<br /><br /> MSI oluşturmak için çözümünüze bir kurulum projesi eklemeniz gerekir.<br /><br /> Daha fazla bilgi için bkz. [MSI dosyası kullanarak DSL dağıtma](#msi).|

## <a name="Installing"></a>VSX kullanarak DSL yükleme ve kaldırma

Bu yöntem tarafından DSL yüklendiğinde, Kullanıcı Visual Studio içinden bir DSL dosyası açabilir, ancak dosya Windows Gezgini ' nden açılamaz.

### <a name="to-install-a-dsl-by-using-the-vsx"></a>VSX kullanarak bir DSL yüklemek için

1. DSL paketi projeniz tarafından oluşturulan **. vsix** dosyasını bulun:

   1. **Çözüm Gezgini**, **DslPackage** projesine sağ tıklayın ve ardından **Dosya Gezgini 'nde klasörü aç**' a tıklayın.

   2. Dosya **bin\\\*\\** _projem_' i bulun **. DslPackage. vsix**

2. **. Vsix** dosyasını, DSL 'yi yüklemek istediğiniz hedef bilgisayara kopyalayın. Bu, kendi bilgisayarınız veya başka bir tane olabilir.

   - Hedef bilgisayar, çalışma zamanında DSLs 'yi destekleyen [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] sürümlerinden birine sahip olmalıdır. Daha fazla bilgi için bkz. [görselleştirme Için desteklenen Visual Studio sürümleri & modelleme SDK](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md).

   - Hedef bilgisayar, **DslPackage\source.Extensions.manifest**Içinde belirtilen Visual Studio sürümlerinden birine sahip olmalıdır.

3. Hedef bilgisayarda **. vsix** dosyasına çift tıklayın.

    **Visual Studio Uzantı Yükleyicisi** açılır ve uzantıyı yüklüyor.

4. [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]başlatın veya yeniden başlatın.

5. DSL 'yi test etmek için Visual Studio 'Yu kullanarak DSL 'niz için tanımladığınız uzantıya sahip yeni bir dosya oluşturun.

### <a name="to-uninstall-a-dsl-that-was-installed-by-using-vsx"></a>VSX kullanılarak yüklenen bir DSL 'yi kaldırmak için

1. **Araçlar** menüsünde **Uzantılar ve güncelleştirmeler**' i seçin.

2. **Yüklü uzantıları**genişletin.

3. DSL 'nin tanımlandığı uzantıyı seçin ve ardından **Kaldır**' a tıklayın.

   Nadiren, hatalı bir uzantı yükleme başarısız olur ve hata penceresinde bir rapor oluşturur, ancak Uzantı Yöneticisi 'nde görünmez. Bu durumda, dosyayı öğesinden silerek uzantıyı kaldırabilirsiniz:

   *LocalAppData* **\Microsoft\VisualStudio\10.0\Extensions**

## <a name="msi"></a>MSI içinde DSL dağıtma
 DSL 'niz için bir MSI (Windows Installer) dosyası tanımlayarak, kullanıcıların Windows Gezgini 'nden DSL dosyalarını açmasına izin verebilirsiniz. Ayrıca, dosya adı uzantınızla bir simge ve kısa açıklama ilişkilendirebilirsiniz. Buna ek olarak, MSI DSL dosyalarını doğrulamak için kullanılabilen bir XSD 'yi de yükleyebilir. İsterseniz, diğer bileşenleri MSI 'ye aynı anda yüklenecek şekilde ekleyebilirsiniz.

 MSI dosyaları ve diğer dağıtım seçenekleri hakkında daha fazla bilgi için bkz. [uygulamaları, hizmetleri ve bileşenleri dağıtma](../deployment/deploying-applications-services-and-components.md).

 Bir MSI oluşturmak için, Visual Studio çözümünüze bir kurulum projesi eklersiniz. Bir kurulum projesi oluşturmanın en kolay yöntemi, [VMSDK sitesinden](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)indirebileceğiniz CreateMsiSetupProject.tt şablonunu kullanmaktır.

### <a name="to-deploy-a-dsl-in-an-msi"></a>MSI içinde DSL dağıtmak için

1. Uzantı bildiriminde `InstalledByMsi` ayarlayın. Bu, VSX 'in MSI dışında yüklenmesini ve kaldırılmasını engeller. Bu, MSI 'ye diğer bileşenleri dahil etmek için önemlidir.

   1. Open DslPackage\source.extension.tt

   2. `<SupportedProducts>`önce aşağıdaki satırı ekleyin:

       ```xml
       <InstalledByMsi>true</InstalledByMsi>
       ```

2. Windows Gezgini 'nde DSL 'yi temsil edecek bir simge oluşturun veya düzenleyin. Örneğin, **Dslpackage\resources\file.exe** dosyasını düzenleyin

3. DSL 'nizin aşağıdaki özniteliklerinin doğru olduğundan emin olun:

   - DSL Gezgini ' nde kök düğümüne tıklayın ve Özellikler penceresi ' de şunları gözden geçirin:

       - Açıklama

       - Sürüm

   - **Düzenleyici** düğümüne tıklayın ve Özellikler penceresi **simgesine**tıklayın. Değeri **Dslpackage\resources**içindeki **File. ico** gibi bir simge dosyasına başvuracak şekilde ayarlayın.

   - **Yapı** menüsünde **Configuration Manager**açın ve derlemek istediğiniz yapılandırmayı (örneğin, **yayın** veya **hata ayıklama**) seçin.

4. [Görselleştirme ve modelleme SDK 'sı giriş sayfasına](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)gidin ve **indirmeler** sekmesinden **CreateMsiSetupProject.tt**indirin.

5. DSL projenize **CreateMsiSetupProject.tt** ekleyin.

    Visual Studio, **CreateMsiSetupProject. VDPROJ**adlı bir dosya oluşturur.

6. Windows Gezgini 'nde, DSL\\*. VDPROJ öğesini kurulum adlı yeni bir klasöre kopyalayın.

    (İsterseniz, CreateMsiSetupProject.tt artık DSL projenizden dışarıda bırakabilirsiniz.)

7. **Çözüm Gezgini**, mevcut bir proje olarak **\*. VDPROJ kurulum\\** ekleyin.

8. **Proje** menüsünde **Proje bağımlılıkları**' na tıklayın.

    **Proje bağımlılıkları** iletişim kutusunda Kurulum projesini seçin.

    **DslPackage**seçeneğinin yanındaki kutuyu seçin.

9. Çözümü yeniden derleyin.

10. Windows Gezgini 'nde, Kurulum projenizde oluşturulan MSI dosyasını bulun.

     MSI dosyasını, DSL 'yi yüklemek istediğiniz bir bilgisayara kopyalayın. MSI dosyasına çift tıklayın. Yükleyici çalışır.

11. Hedef bilgisayarda, DSL 'niz dosya uzantısına sahip yeni bir dosya oluşturun. Şunları doğrulayın:

    - Windows Gezgini liste görünümünde dosya, tanımladığınız simge ve açıklama ile görüntülenir.

    - Dosyaya çift tıkladığınızda, Visual Studio başlar ve DSL Düzenleyicisi 'ndeki DSL dosyasını açar.

    İsterseniz, Kurulum projesini metin şablonunu kullanmak yerine el ile oluşturabilirsiniz. Bu yordamı içeren bir anlatım için [görselleştirme ve modelleme SDK laboratuvarının](https://code.msdn.microsoft.com/DSLToolsLab/Release/ProjectReleases.aspx?ReleaseId=4207)5. bölümüne bakın.

### <a name="to-uninstall-a-dsl-that-was-installed-from-an-msi"></a>MSI 'dan yüklenmiş bir DSL 'yi kaldırmak için

1. Windows 'ta, **Programlar ve Özellikler** denetim masasını açın.

2. DSL 'yi kaldırın.

3. Visual Studio'yu yeniden başlatın.
