---
title: DSL'nin MSI ve VSIX Dağıtımı
description: Kendi bilgisayarınıza veya diğer bilgisayarlara etki alanına özgü bir dili (DSL) nasıl yükleyebilirsiniz?
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 65df491989278f768f44cb0f768a216e082a6570
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122100835"
---
# <a name="msi-and-vsix-deployment-of-a-dsl"></a>DSL'nin MSI ve VSIX Dağıtımı
Etki alanına özgü bir dili kendi bilgisayarınıza veya diğer bilgisayarlara yükleyebilirsiniz. Visual Studio bilgisayarda yüklü olması gerekir.

## <a name="choosing-between-vsix-and-msi-deployment"></a><a name="which"></a> VSIX ile MSI Dağıtımı arasında seçim
 Etki alanına özgü dil dağıtmanın iki yöntemi vardır:

|Yöntem|Avantajlar|
|-|-|
|VSX (Visual Studio Uzantısı)|Dağıtımı çok kolay: DslPackage projesinden **.vsix** dosyasını kopyalayıp yürütün.<br /><br /> Daha fazla bilgi için [bkz. VSX kullanarak DSL Yükleme ve Kaldırma.](#Installing)|
|MSI (yükleyici dosyası)|- Bir DSL dosyasına çift Visual Studio kullanıcının bir dosyayı açması için izin verir.<br />- Bir simgeyi hedef bilgisayarda DSL dosya türüyle ilişkilendirin.<br />- Dsl dosya türüyle bir XSD (XML şeması) ilişkilendirin. Bu, dosya bir dosyaya yüklendiğinde uyarılardan Visual Studio.<br /><br /> MSI oluşturmak için çözümünüze bir kurulum projesi eklemeniz gerekir.<br /><br /> Daha fazla bilgi için [bkz. MSI dosyası kullanarak DSL dağıtma.](#msi)|

## <a name="install-and-uninstall-a-dsl-by-using-the-vsx"></a><a name="Installing"></a> VSX kullanarak DSL Yükleme ve Kaldırma

DSL'niz bu yöntem tarafından yüklenirken, kullanıcı bir DSL dosyasını Visual Studio içinde açabilir, ancak dosya Windows Explorer'dan açamaz.

### <a name="to-install-a-dsl-by-using-the-vsx"></a>VSX kullanarak DSL yüklemek için

1. DSL Paketi projeniz tarafından inşa edilen **.vsix** dosyasını bulun:

   1. Bu **Çözüm Gezgini** **DslPackage** projesine sağ tıklayın ve ardından Dosya Gezgini'de **Klasörü Aç'a tıklayın.**

   2. **\\ \* \\**_YourProject dosya binini_**bulun. DslPackage.vsix**

2. **.vsix dosyasını** DSL yüklemek istediğiniz hedef bilgisayara kopyalayın. Bu, kendi bilgisayarınız veya başka bir bilgisayarınız olabilir.

   - Hedef bilgisayarda, çalışma zamanında [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] DSL'leri destekleyen sürümlerinden biri olmalıdır. Daha fazla bilgi için [bkz. Görselleştirme Visual Studio Için Desteklenen sürümler & SDK'sı.](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md)

   - Hedef bilgisayarda **DslPackage\source.extensions.manifest** içinde belirtilen Visual Studio sürümlerinden biri olmalıdır.

3. Hedef bilgisayarda **.vsix dosyasına çift** tıklayın.

    **Visual Studio Yükleyicisi** açılır ve uzantı yüklenir.

4. başlatın veya yeniden [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] başlatın.

5. DSL'i test etmek Visual Studio kullanarak DSL'niz için tanımlandığı uzantıya sahip yeni bir dosya oluşturun.

### <a name="to-uninstall-a-dsl-that-was-installed-by-using-vsx"></a>VSX kullanılarak yüklenmiş bir DSL'i kaldırmak için

1. Araçlar menüsünde **Uzantılar** ve **Güncelleştirmeler'i seçin.**

2. Yüklü **Uzantılar'a genişletin.**

3. DSL'nin tanımlandığı uzantıyı seçin ve ardından Kaldır'a **tıklayın.**

   Nadiren, hatalı bir uzantı yüklenemezse ve hata penceresinde bir rapor oluşturur, ancak Uzantı Yöneticisi'nde görünmez. Bu durumda, dosyayı silerek uzantıyı kaldırabilirsiniz:

   *LocalAppData* **\Microsoft\VisualStudio\10.0\Extensions**

## <a name="deploying-a-dsl-in-an-msi"></a><a name="msi"></a> MSI'de DSL dağıtma
 DSL'niz için bir MSI (Windows Yükleyicisi) dosyası tanımlayarak, kullanıcıların DSL dosyalarını Windows açabilirsiniz. Bir simgeyi ve kısa açıklamayı dosya adı uzantınız ile de ilişkilendirilebilirsiniz. Ayrıca, MSI DSL dosyalarını doğrulamak için kullanılan bir XSD yükleyebilir. Güncelleştirmeyi yapmak için MSI'ye aynı anda yüklenecek olan diğer bileşenleri güncelleştirmeyi de güncelleştirmeyi kabul etmek gerekir.

 MSI dosyaları ve diğer dağıtım seçenekleri hakkında daha fazla bilgi için [bkz. Uygulamaları, Hizmetleri ve Bileşenleri Dağıtma.](../deployment/deploying-applications-services-and-components.md)

 MSI oluşturmak için, Visual Studio çözümünüze bir Kurulum Visual Studio eklersiniz. Kurulum projesi oluşturmanın en kolay yöntemi, [VMSDK](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)sitesinden indirerek CreateMsiSetupProject.tt şablonu kullanmaktır.

### <a name="to-deploy-a-dsl-in-an-msi"></a>MSI'de DSL dağıtmak için

1. Uzantı `InstalledByMsi` bildiriminde ayarlayın. Bu, VSX'in MSI dışında yük devrederek kaldırılmasını önler. MSI'ye diğer bileşenleri dahil etmek için bu önemlidir.

   1. Open DslPackage\source.extension.tt

   2. önce aşağıdaki satırı `<SupportedProducts>` ekler:

       ```xml
       <InstalledByMsi>true</InstalledByMsi>
       ```

2. WINDOWS Explorer'da DSL'nizi temsil edecek bir simge oluşturun veya düzenleyin. Örneğin **DslPackage\Resources\File.ico dosyasını düzenleyin**

3. DSL'nizin aşağıdaki özniteliklerinin doğru olduğundan emin olun:

   - DSL Gezgini'nde kök düğüme tıklayın ve Özellikler penceresi gözden geçirebilirsiniz:

       - Açıklama

       - Sürüm

   - Düzenleyici **düğümüne** tıklayın ve Özellikler penceresi Simgesi'ne **tıklayın.** **DslPackage\Resources** içinde **File.ico** gibi bir simge dosyasına başvuru yapmak için değeri ayarlayın

   - Build **(Derleme)** menüsünde **Yapılandırma Yöneticisi** açın ve derlemek istediğiniz yapılandırmayı (Yayın veya Hata Ayıklama **gibi)** **seçin.**

4. Görselleştirme ve [Modelleme SDK'sı giriş sayfasına gidin](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)ve İndirmeler sekmesinden CreateMsiSetupProject.tt.  

5. Dsl **CreateMsiSetupProject.tt** ekleme.

    Visual Studio **CreateMsiSetupProject.vdproj adlı bir dosya oluşturacak.**

6. Bu Windows Dsl \\ *.vdproj dosyasını Kurulum adlı yeni bir klasöre kopyalayın.

    (Sınsın, artık Dsl projenizin CreateMsiSetupProject.tt dışlamanız gerekir.)

7. Bu **Çözüm Gezgini,** Setup **\\ \* .vdproj'u mevcut** bir proje olarak ekleyin.

8. Project **menüsünde** Bağımlılıklar'Project **tıklayın.**

    **Bağımlılıklar Project** kutusunda kurulum projesini seçin.

    **DslPackage'ın yanındaki kutuyu seçin.**

9. Çözümü yeniden derleyin.

10. Windows Gezgini'nde, Kurulum projenizin yerleşik MSI dosyasını bulun.

     MSI dosyasını DSL'nizi yüklemek istediğiniz bilgisayara kopyalayın. MSI dosyasına çift tıklayın. Yükleyici çalışır.

11. Hedef bilgisayarda, DSL'nizin dosya uzantısına sahip yeni bir dosya oluşturun. Şunları doğrulayın:

    - Gezgin Windows görünümünde dosya, tanımlandığı simge ve açıklamayla birlikte görüntülenir.

    - Dosyaya çift tıklarsanız, Visual Studio başlar ve DSL dosyasını DSL düzenleyicisinde açar.

    Tercih ederseniz, metin şablonunu kullanmak yerine Kurulum projesini el ile oluşturabilirsiniz. Bu yordamı içeren bir kılavuz için Görselleştirme ve Modelleme SDK Laboratuvarı'nın [5. Bölüm'e bakın.](https://code.msdn.microsoft.com/DSLToolsLab/Release/ProjectReleases.aspx?ReleaseId=4207)

### <a name="to-uninstall-a-dsl-that-was-installed-from-an-msi"></a>MSI'den yüklenmiş bir DSL'i kaldırmak için

1. Bu Windows Programlar ve **Özellikler denetim panelini** açın.

2. DSL'i kaldırın.

3. Visual Studio’yu yeniden başlatın.
