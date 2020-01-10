---
title: Modelleme uzantısı tanımlama ve yüklemeyi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending
- UML model, extending
ms.assetid: 82a58dc5-c7cf-4521-a6da-7ff09cd0de9d
caps.latest.revision: 39
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c38150dd84ef8898b2aa894a614dfb79e289b593
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850447"
---
# <a name="define-and-install-a-modeling-extension"></a>Modelleme uzantısı tanımlama ve yükleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 'da, modelleme diyagramları için uzantıları tanımlayabilirsiniz. Bu şekilde, diyagramları ve modelleri kendi gereksinimlerinize uyarlayabilirsiniz. Örneğin, menü komutlarını, UML profillerini, doğrulama kısıtlamalarını ve araç kutusu öğelerini tanımlayabilirsiniz. Tek bir uzantıda birkaç bileşen tanımlayabilirsiniz. Ayrıca, bu uzantıları [Visual Studio Tümleştirme Uzantısı (VSIX)](https://msdn.microsoft.com/library/dd393694(VS.100).aspx)biçimindeki diğer Visual Studio kullanıcılarına dağıtabilirsiniz. Visual Studio 'da VSıX projesi kullanarak bir VSıX oluşturabilirsiniz.

## <a name="requirements"></a>Gereksinimler
 [Gereksinimlere](../modeling/extend-uml-models-and-diagrams.md#Requirements)bakın.

 Visual Studio 'nun hangi sürümlerinin bu özelliği desteklediğini görmek için bkz. [mimari ve modelleme araçları Için sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="creating-a-modeling-extension-solution"></a>Modelleme uzantısı çözümü oluşturma
 Bir modelleme uzantısı tanımlamak için şu projeleri içeren bir çözüm oluşturmanız gerekir:

- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Tümleştirme Uzantısı (VSıX) projesi. Bu, uzantınızın bileşenleri için yükleyici olarak davranan bir dosya oluşturur.

- Program kodu içeren bileşenler için gereken bir sınıf kitaplığı projesi.

  Birden çok bileşeni olan bir uzantı oluşturmak isterseniz, bunları tek bir çözümde geliştirebilirsiniz. Yalnızca bir VSıX projesine ihtiyacınız vardır.

  Özel araç kutusu öğeleri ve özel UML profilleri gibi kod gerektirmeyen bileşenler, ayrı sınıf kitaplığı projeleri kullanılmadan doğrudan VSıX projesine eklenebilir. Program kodu gerektiren bileşenler ayrı bir sınıf kitaplığı projesinde daha kolay tanımlanır. Kod gerektiren, hareket işleyicileri, menü komutları ve doğrulama kodu içeren bileşenler.

#### <a name="to-create-a-class-library-project-for-menu-commands-gesture-handlers-or-validation"></a>Menü komutları, hareket işleyicileri veya doğrulama için bir sınıf kitaplığı projesi oluşturmak için

1. **Dosya** menüsünde, **Yeni**, **Proje**' yi seçin.

2. **Yüklü şablonlar**altında, **görsel C#**  veya **Visual Basic**' yi seçin ve ardından **sınıf kitaplığı**' nı seçin.

#### <a name="to-create-a-vsix-project"></a>VSıX projesi oluşturmak için

1. Kod içeren bir bileşen oluşturuyorsanız, önce sınıf kitaplığı projesinin oluşturulması en kolay yoldur. Kodunuzu bu projeye ekleyeceksiniz.

2. Bir VSIX projesi oluşturun.

    1. **Çözüm Gezgini**, çözümün kısayol menüsünde, **Ekle**, **Yeni proje**' yi seçin.

    2. **Yüklü şablonlar**altında,  **C# görsel** veya **Visual Basic**' ı genişletin, ardından **genişletilebilirlik**' i seçin. Orta sütunda **VSIX projesi**' ni seçin.

3. VSıX projesini çözümün başlangıç projesi olarak ayarlayın.

    - Çözüm Gezgini, VSıX projesinin kısayol menüsünde **Başlangıç projesi olarak ayarla**' yı seçin.

4. Açık **kaynak. Extension. valtmanifest**. Dosya, bildirim düzenleyicisinde açılır.

5. **Meta veri** SEKMESINDE, VSIX 'in adını ve tanımlayıcı alanlarını ayarlayın.

6. **Hedefleri yüklensin** sekmesinde, **Yeni** ' yi seçin ve Visual Studio sürümlerini hedef olarak ayarlayın.

7. **Varlıklar** sekmesinde, bileşenlerinizi Visual Studio uzantısına ekleyin.

    1. **Yeni**'yi seçin.

    2. Kod içeren bir bileşen için **yeni varlık Ekle** iletişim kutusunda bu alanları ayarlayın:

        |||
        |-|-|
        |**Tür** =|**Microsoft. VisualStudio. MefComponent**|
        |**Kaynak** =|**Geçerli çözümdeki bir proje**|
        |**Project** =|*Sınıf kitaplığı projeniz*|
        |**Bu klasöre ekle** =|*olmamalıdır*|

         Diğer bileşen türleri için, sonraki bölümde bulunan bağlantılara bakın.

## <a name="developing-the-component"></a>Bileşen geliştirme
 Bir menü komutu veya hareket işleyicisi gibi her bir bileşen için ayrı bir işleyici tanımlamanız gerekir. Aynı sınıf kitaplığı projesine çeşitli işleyiciler yerleştirebilirsiniz. Aşağıdaki tabloda farklı tür işleyici özetlenmektedir.

|Uzantı türü|Konu|Her bileşenin genellikle nasıl bildirildiği|
|--------------------|-----------|----------------------------------------------|
|Menü komutu|[Modelleme diyagramında menü komutu tanımlama](../modeling/define-a-menu-command-on-a-modeling-diagram.md)|`[ClassDesignerExtension]`<br /><br /> `// or other diagram types`<br /><br /> `[Export(typeof(ICommandExtension))]`<br /><br /> `public class MyCommand : ICommandExtension`<br /><br /> `{...`|
|Sürükleyip bırakma veya çift tıklama|[Modelleme diyagramında hareket işleyicisi tanımlama](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md)|`[ClassDesignerExtension]`<br /><br /> `// or other diagram types`<br /><br /> `[Export(typeof(IGestureExtension))]`<br /><br /> `public class MyGesture : IGestureExtension`<br /><br /> `{...`|
|Doğrulama kısıtlaması|[UML modelleri için doğrulama kısıtlamaları tanımlama](../modeling/define-validation-constraints-for-uml-models.md)|`[Export(typeof(     System.Action<ValidationContext, object>))]`<br /><br /> `[ValidationMethod(ValidationCategories.Save`<br /><br /> `&#124; ValidationCategories.Menu)]`<br /><br /> `public void ValidateSomething`<br /><br /> `(ValidationContext context, IClassifier elementToValidate)`<br /><br /> `{...}`|
|Çalışma öğesi bağlantısı olay işleyicisi|[İş öğesi bağlantı işleyicisi tanımlama](../modeling/define-a-work-item-link-handler.md)|`[Export(typeof(ILinkedWorkItemExtension))]`<br /><br /> `public class MyWorkItemEventHandler : ILinkedWorkItemExtension`<br /><br /> `{...`|
|UML profili|[UML’yi genişletmek için profil tanımlama](../modeling/define-a-profile-to-extend-uml.md)|(Tanımlanması için)|
|Araç kutusu öğesi|[Özel bir modelleme araç kutusu öğesi tanımlama](../modeling/define-a-custom-modeling-toolbox-item.md)|(Tanımlanması için)|

## <a name="running-an-extension-during-its-development"></a>Geliştirme sırasında bir uzantıyı çalıştırma

#### <a name="to-run-an-extension-during-its-development"></a>Geliştirme sırasında bir uzantıyı çalıştırmak için

1. [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] **hata ayıklama** menüsünde, **hata ayıklamayı Başlat**' ı seçin.

     Proje oluşturulur ve yeni bir [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] örneği deneysel modda başlatılır.

    - Alternatif olarak, **hata ayıklama olmadan Başlat**' ı seçebilirsiniz. Bu, programı başlatmak için geçen süreyi azaltır.

2. Visual Studio 'nun deneysel örneğinde bir modelleme projesi oluşturun veya açın ve bir diyagram oluşturun veya açın.

     Uzantınız yüklenip çalıştırılır.

3. **Hata ayıklama olmadan Başlat** ' ı kullandıysanız, ancak hata ayıklayıcıyı kullanmak Istiyorsanız, Visual Studio 'nun ana örneğine dönün. **Hata Ayıkla** menüsünde, **İşleme İliştir ' e**tıklayın. İletişim kutusunda, **devenv**program adına sahip, Visual Studio 'nun Deneysel örneğini seçin.

## <a name="Installing"></a>Uzantı yükleme ve kaldırma
 Uzantınızı kendi bilgisayarınızda veya diğer bilgisayarlarda Visual Studio 'nun ana örneğinde çalıştırmak için aşağıdaki adımları gerçekleştirin.

1. Bilgisayarınızda, uzantı projeniz tarafından oluşturulan **. vsix** dosyasını bulun.

    1. **Çözüm Gezgini**' de, projenizin kısayol menüsünde **klasörü Windows Gezgini 'nde aç**' ı seçin.

    2. Dosya **bin\\\*bulun \\** _yourproject_ **. vsix**

2. **. Vsix** dosyasını, uzantıyı yüklemek istediğiniz hedef bilgisayara kopyalayın. Bu, kendi bilgisayarınız veya başka bir tane olabilir.

    - Hedef bilgisayar, **kaynak. Extension. valtmanifest**'In **Yükleme hedefleri** sekmesinde belirttiğiniz Visual Studio sürümlerinden birine sahip olmalıdır.

3. Hedef bilgisayarda, örneğin çift tıklayarak **. vsix** dosyasını açın.

     **Visual Studio Uzantı Yükleyicisi** açılır ve uzantıyı yüklüyor.

4. Visual Studio 'Yu başlatın veya yeniden başlatın.

#### <a name="to-uninstall-an-extension"></a>Bir uzantıyı kaldırmak için

1. Üzerinde **Araçları** menüsünü tıklatın **Uzantılar ve güncelleştirmeler**.

2. **Yüklü uzantıları**genişletin.

3. Uzantıyı seçin ve ardından **Kaldır**' a tıklayın.

   Nadiren, hatalı bir uzantı yükleme başarısız olur ve hata penceresinde bir rapor oluşturur, ancak Uzantı Yöneticisi 'nde görünmez. Bu durumda, dosyayı şu konumda silerek uzantıyı kaldırabilirsiniz: *% LocalAppData%* genellikle *DriveName*: \Users\\*UserName*\AppData\Local:

   *% LocalAppData%* **\microsoft\visualstudio\\[sürüm] \Extensions**

## <a name="see-also"></a>Ayrıca Bkz.
 [UML genişletmek için profil tanımlama](../modeling/define-a-profile-to-extend-uml.md) [Özel Modelleme Araç kutusu öğesi](../modeling/define-a-custom-modeling-toolbox-item.md) [UML modelleriyle ilgili doğrulama kısıtlamalarını tanımlama](../modeling/define-validation-constraints-for-uml-models.md) [Modelleme Diyagramında Menü komutu tanımlama](../modeling/define-a-menu-command-on-a-modeling-diagram.md)
