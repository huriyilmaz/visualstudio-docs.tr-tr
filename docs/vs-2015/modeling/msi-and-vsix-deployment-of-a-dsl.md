---
title: DSL 'nin MSI ve VSıX dağıtımı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 6ce16f06-1978-4e19-8cdc-441ee65a3fb2
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4917fc81f439ef0185a753fb1c4c85e460eb7681
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297735"
---
# <a name="msi-and-vsix-deployment-of-a-dsl"></a>DSL'nin MSI ve VSIX Dağıtımı
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kendi bilgisayarınıza veya diğer bilgisayarlara, etki alanına özgü bir dil yükleyebilirsiniz. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] hedef bilgisayara zaten yüklenmiş olmalıdır.

## <a name="which"></a>VSıX ve MSI dağıtımı arasında seçim yapma
 Etki alanına özgü dil dağıtmanın iki yöntemi vardır:

|Yöntem|Yararları|
|------------|--------------|
|VSX ([!INCLUDE[vsprvs](../includes/vsprvs-md.md)] uzantısı)|Dağıtım çok kolay: **. vsix** dosyasını DslPackage projesinden kopyalayın ve yürütün.<br /><br /> Daha fazla bilgi için bkz. [VSX kullanarak DSL yükleme ve kaldırma](#Installing).|
|MSI (yükleyici dosyası)|-Kullanıcının bir DSL dosyasına çift tıklayarak [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] açmasına izin verir.<br />-Bir simgeyi hedef bilgisayardaki DSL dosyası türüyle ilişkilendirir.<br />-Bir XSD (XML Şeması) DSL dosya türüyle ilişkilendirir. Bu, dosya [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]yüklendiğinde uyarıları önler.<br /><br /> MSI oluşturmak için çözümünüze bir kurulum projesi eklemeniz gerekir.<br /><br /> Daha fazla bilgi için bkz. [MSI dosyası kullanarak DSL dağıtma](#msi).|

## <a name="Installing"></a>VSX kullanarak DSL yükleme ve kaldırma
 Bu yöntem tarafından DSL yüklendiğinde, Kullanıcı [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]içinden bir DSL dosyası açabilir, ancak dosya Windows Gezgini ' nden açılamaz.

#### <a name="to-install-a-dsl-by-using-the-vsx"></a>VSX kullanarak bir DSL yüklemek için

1. Bilgisayarınızda, DSL paketi projeniz tarafından oluşturulan **. vsix** dosyasını bulun.

    1. **Çözüm Gezgini**, **DslPackage** projesine sağ tıklayın ve ardından **klasörü Windows Gezgini 'nde aç**' a tıklayın.

    2. Dosya **bin\\\*\\** _projem_' i bulun **. DslPackage. vsix**

2. **. Vsix** dosyasını, DSL 'yi yüklemek istediğiniz hedef bilgisayara kopyalayın. Bu, kendi bilgisayarınız veya başka bir tane olabilir.

    - Hedef bilgisayar, çalışma zamanında DSLs 'yi destekleyen [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] sürümlerinden birine sahip olmalıdır. Daha fazla bilgi için bkz. [görselleştirme Için desteklenen Visual Studio sürümleri & modelleme SDK](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md).

    - Hedef bilgisayar, **DslPackage\source.Extensions.manifest**içinde belirtilen [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sürümlerinden birine sahip olmalıdır.

3. Hedef bilgisayarda **. vsix** dosyasına çift tıklayın.

     **Visual Studio Uzantı Yükleyicisi** açılır ve uzantıyı yüklüyor.

4. [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]başlatın veya yeniden başlatın.

5. DSL 'yi test etmek için [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] kullanarak DSL 'niz için tanımladığınız uzantıya sahip yeni bir dosya oluşturun.

#### <a name="to-uninstall-a-dsl-that-was-installed-by-using-vsx"></a>VSX kullanılarak yüklenen bir DSL 'yi kaldırmak için

1. **Araçlar** menüsünde, **Uzantı Yöneticisi**' ne tıklayın.

2. **Yüklü uzantıları**genişletin.

3. DSL 'nin tanımlandığı uzantıyı seçin ve ardından **Kaldır**' a tıklayın.

   Nadiren, hatalı bir uzantı yükleme başarısız olur ve hata penceresinde bir rapor oluşturur, ancak Uzantı Yöneticisi 'nde görünmez. Bu durumda, dosyayı öğesinden silerek uzantıyı kaldırabilirsiniz:

   *LocalAppData* **\Microsoft\VisualStudio\10.0\Extensions**

## <a name="msi"></a>MSI içinde DSL dağıtma
 DSL 'niz için bir MSI (Windows Installer) dosyası tanımlayarak, kullanıcıların Windows Gezgini 'nden DSL dosyalarını açmasına izin verebilirsiniz. Ayrıca, dosya adı uzantınızla bir simge ve kısa açıklama ilişkilendirebilirsiniz. Buna ek olarak, MSI DSL dosyalarını doğrulamak için kullanılabilen bir XSD 'yi de yükleyebilir. İsterseniz, diğer bileşenleri MSI 'ye aynı anda yüklenecek şekilde ekleyebilirsiniz.

 MSI dosyaları ve diğer dağıtım seçenekleri hakkında daha fazla bilgi için bkz. [uygulamaları, hizmetleri ve bileşenleri dağıtma](../deployment/deploying-applications-services-and-components.md).

 Bir MSI oluşturmak için [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] çözümünüze bir kurulum projesi eklersiniz. Bir kurulum projesi oluşturmanın en kolay yöntemi, [VMSDK sitesinden](https://go.microsoft.com/fwlink/?LinkID=186128)indirebileceğiniz CreateMsiSetupProject.tt şablonunu kullanmaktır.

#### <a name="to-deploy-a-dsl-in-an-msi"></a>MSI içinde DSL dağıtmak için

1. Uzantı bildiriminde `InstalledByMsi` ayarlayın. Bu, VSX 'in MSI dışında yüklenmesini ve kaldırılmasını engeller. Bu, MSI 'ye diğer bileşenleri dahil etmek için önemlidir.

   1. Open DslPackage\source.extension.tt

   2. `<SupportedProducts>`önce aşağıdaki satırı ekleyin:

       ```
       <InstalledByMsi>true</InstalledByMsi>
       ```

2. Windows Gezgini 'nde DSL 'yi temsil edecek bir simge oluşturun veya düzenleyin. Örneğin, **Dslpackage\resources\file.exe** dosyasını düzenleyin

3. DSL 'nizin aşağıdaki özniteliklerinin doğru olduğundan emin olun:

   - DSL Gezgini ' nde kök düğümüne tıklayın ve Özellikler penceresi ' de şunları gözden geçirin:

       - Açıklama

       - Version

   - **Düzenleyici** düğümüne tıklayın ve Özellikler penceresi **simgesine**tıklayın. Değeri **Dslpackage\resources**içindeki **File. ico** gibi bir simge dosyasına başvuracak şekilde ayarlayın.

   - **Yapı** menüsünde **Configuration Manager**açın ve derlemek istediğiniz yapılandırmayı (örneğin, **yayın** veya **hata ayıklama**) seçin.

4. [Görselleştirme ve modelleme SDK 'sı giriş sayfasına](https://go.microsoft.com/fwlink/?LinkID=186128)gidin ve **indirmeler** sekmesinden **CreateMsiSetupProject.tt**indirin.

5. DSL projenize **CreateMsiSetupProject.tt** ekleyin.

    [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], **Createmsısetupproject. VDPROJ**adlı bir dosya oluşturacak.

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

    - Dosyayı çift tıklattığınızda [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] başlatılır ve DSL dosyasını DSL düzenleyicisinde açar.

    İsterseniz, Kurulum projesini metin şablonunu kullanmak yerine el ile oluşturabilirsiniz. Bu yordamı içeren bir anlatım için [görselleştirme ve modelleme SDK laboratuvarının](https://go.microsoft.com/fwlink/?LinkId=208878)5. bölümüne bakın.

#### <a name="to-uninstall-a-dsl-that-was-installed-from-an-msi"></a>MSI 'dan yüklenmiş bir DSL 'yi kaldırmak için

1. Windows 'ta, **Programlar ve Özellikler** denetim masasını açın.

2. DSL 'yi kaldırın.

3. Visual Studio'yu yeniden başlatın.
