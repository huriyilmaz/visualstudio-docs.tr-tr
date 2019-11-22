---
title: UML modelleme projeleri ve diyagramları oluşturma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.addnewdiagramdialog
- vs.teamarch.createnewmodelingprojectdialog
helpviewer_keywords:
- projects [Visual Studio ALM], modeling
- diagrams - modeling, modeling
- modeling diagrams
- projects, UML
- UML, deleting diagrams
- UML
- UML diagrams, adding
- UML, projects
- Visual Studio ALM, modeling projects
- modeling projects
- UML diagrams
- projects, modeling
ms.assetid: c178b04b-4fd2-4bed-97e3-d793dae8649c
caps.latest.revision: 50
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d5884dcd3f9e3cb8f1910d2e23ec80f910ed2fc9
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301008"
---
# <a name="create-uml-modeling-projects-and-diagrams"></a>UML modelleme projeleri ve diyagramları oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

UML modelleri, yazılım sistemlerini anlamanıza, tartışmanıza ve tasarlamanıza yardımcı olur. Visual Studio, en sık kullanılan UML diyagramlarından beş tane için şablon sağlar: etkinlik, sınıf, bileşen, sıra ve kullanım örneği. Ayrıca, sisteminizin yapısını tanımlamanıza yardımcı olan katman diyagramları da oluşturabilirsiniz.

 UML modelleme diyagramları ve katman diyagramları yalnızca bir modelleme projesi içinde bulunabilir. Her modelleme projesi, paylaşılan bir UML modeli ve birkaç UML diyagramı içerir. Her diyagram, modelin kısmi görünümüdür. UML model, UML diyagramlarındaki tüm öğeleri içerir ve UML Model Gezgini kullanılarak görüntülenebilir. Modeller ve diyagramlarla ilişkileri hakkında daha fazla bilgi için bkz. [UML modellerini ve diyagramlarını düzenleme](../modeling/edit-uml-models-and-diagrams.md). Sürüm denetimi altındaki modelleme projeleri hakkında daha fazla bilgi için bkz. [sürüm denetimi altındaki modelleri ve diyagramları yönetme](../modeling/manage-models-and-diagrams-under-version-control.md) ve [modelleme çözümünüzü yapılandırma](../modeling/structure-your-modeling-solution.md)

> [!NOTE]
> Program kodunu görselleştirmek için kullanılan, .NET sınıf diyagramı olan başka bir diyagram türü vardır. Daha fazla bilgi için bkz. [sınıfları ve türleri tasarlama ve görüntüleme](https://go.microsoft.com/fwlink/?LinkId=142231).

## <a name="CreatingModelingDiagrams"></a>Modelleme projesinde diyagram oluşturma
 Visual Studio 'nun hangi sürümlerinin bu özelliği desteklediğini görmek için bkz. [mimari ve modelleme araçları Için sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

#### <a name="to-create-a-diagram-and-add-it-to-a-project"></a>Diyagram oluşturmak ve bir projeye eklemek için

1. **Mimari** menüsünde **Yeni UML veya katman diyagramı**' nı seçin.

2. **Yeni Diyagram Ekle** iletişim kutusunda istediğiniz modelleme diyagramı türüne tıklayın.

    ![Yeni Diyagram Ekle iletişim kutusu](../modeling/media/uml-adddiagram.png "UML_AddDiagram")

3. Yeni Diyagram için bir ad yazın.

4. **Modelleme projesine ekle** kutusunda:

   - Çözümünüzde zaten var olan bir modelleme projesi seçin ve ardından **Tamam**' a tıklayın.

     \- veya -

   1. **Yeni modelleme projesi oluştur**' u seçin ve ardından **Tamam**' a tıklayın.

   2. **Yeni modelleme projesi oluştur** iletişim kutusunda yeni proje için bir ad ve konum yazın ve ardından **Tamam**' a tıklayın.

        ![Yeni modelleme projesi oluştur iletişim kutusu](../modeling/media/uml-createmodel.png "UML_CreateModel")

        Çözümünüz açıksa yeni proje çözüme eklenir. Açık çözümünüz yoksa, yeni bir çözüm için bir ad yazabilirsiniz.

   Zaten bir modelleme projeniz varsa, aşağıdaki yordamı da kullanabilirsiniz.

#### <a name="to-add-a-diagram-to-an-existing-modeling-project"></a>Varolan bir modelleme projesine diyagram eklemek için

1. **Çözüm Gezgini**, modelleme projesi düğümüne tıklayın.

    > [!NOTE]
    > Modelleme projesi **ModelDefinition**adlı bir model tanımı klasörü içerir.

2. **Proje** menüsünde **Yeni öğe Ekle**' ye tıklayın.

3. **Yeni öğe Ekle-** *\<proje adı >* iletişim kutusunda **Şablonlar**' ın altında, modelleme diyagramı türü ' ne tıklayın, örneğin **UML bileşen diyagramı**.

4. Diyagram için bir ad yazın ve ardından **Ekle**' ye tıklayın.

     Modelleme diyagramı açılır ve modelleme projesinde görüntülenir.

    > [!CAUTION]
    > Varolan diyagram dosyalarını başka modelleme projelerine veya çözümdeki diğer konumlara eklemeyin, kopyalamayın veya sürüklemeyin. Bu, diyagramları açtığınızda öğelerin kopyalanmış diyagramlardan veya hataların kaybolmasına neden olur. Diyagram dosyasını oluşturulduğu modelleme projesinden açmanız gerekir. Bunun nedeni, UML diyagramının modelleme projesine ait olan modelin bir görünümüdür. Bir diyagram dosyasını kopyalamak için yeni bir diyagram oluşturun ve sonra öğeleri kaynak diyagramından yeni diyagrama kopyalayın. Daha fazla bilgi için bkz. [modelleme projelerinde ve diyagramlarda sorun giderme](#TroubleshootingModelingProjects).

#### <a name="to-create-a-blank-modeling-project"></a>Boş modelleme projesi oluşturmak için

1. **Dosya** menüsünde, **Yeni**' nin üzerine gelin ve ardından **Proje**' ye tıklayın.

2. **Yeni proje** iletişim kutusunda, **yüklü şablonlar**altında, **modelleme projeleri**' ne tıklayın.

3. Orta pencerede **modelleme projesi**' ne tıklayın.

4. Projeyi adlandırın ve **ad** ve **konum** kutularında bir konum belirtin.

5. Yeni projeyi zaten açık olan bir çözüme eklemek için **çözüm** kutusunda **çözüme Ekle** ' yi seçin; ya da açık herhangi bir çözümü kapatmak için yeni bir çözüm **oluşturun** ve projeyi yeni bir çözüme ekleyin.

## <a name="RemovingModelingDiagrams"></a>Bir projeden modelleme diyagramlarını kaldırma
 Bir diyagramı kalıcı olarak silebilir veya bir projeyi bir projeden geçici olarak dışarıda bırakabilir ve sonra geri yükleyebilirsiniz.

#### <a name="to-permanently-delete-a-diagram-from-a-project"></a>Bir diyagramı bir projeden kalıcı olarak silmek için

- **Çözüm Gezgini**' de, diyagramı temsil eden ana dosyaya sağ tıklayın ve ardından **Sil**' e tıklayın.

     Diyagram projeden ve dosya sisteminden kaldırılır. Diyagramda gösterilen öğeler **UML Model Gezgini**' nden kaldırılmaz.

    > [!NOTE]
    > Her diyagramda iki dosya bulunur, diğeri diğeri bir yan. Örneğin, `CD1`adında bir bileşen diyagramınıza sahipseniz, `CD1.componentdiagram`adlı dosyayı silmelisiniz. `CD1.componentdiagram.layout` adlı yan kuruluş dosyası otomatik olarak silinecek.

#### <a name="to-temporarily-exclude-a-diagram-from-a-project"></a>Bir diyagramı bir projeden geçici olarak dışlamak için

- **Çözüm Gezgini**, diyagram dosyasına sağ tıklayın ve ardından **projeden Dışla**' ya tıklayın.

     Diyagram projeden kaldırılır. Dosya sisteminden kaldırılmaz.

    > [!NOTE]
    > Diyagramda gösterilen öğeler **UML Model Gezgini**' nden kaldırılmaz.

#### <a name="to-restore-a-temporarily-excluded-diagram-to-a-project"></a>Geçici olarak dışlanan bir diyagramı bir projeye geri yüklemek için

1. **Çözüm Gezgini**, modelleme projesi düğümüne tıklayın.

    > [!NOTE]
    > Modelleme projesi **ModelDefinition**adlı bir model tanımı klasörü içerir.

2. **Proje** menüsünde, **Varolan öğe Ekle**' ye tıklayın.

3. **Varolan öğe Ekle** iletişim kutusunda, diyagram dosyasını bulun, dosyayı seçin ve ardından **Ekle**' ye tıklayın.

     Modelleme diyagramı açılır ve modelleme projesinde görüntülenir.

    > [!NOTE]
    > Her diyagramda dosya sisteminde bir dosya çifti bulunur. `.layout`uzantısı olan bir dosya seçmeyin. Ayrıca, Visual Studio birden çok modelleme projesine mevcut UML diyagramları eklemeyi desteklemez. Her diyagram dosyası oluşturulduğu modelleme projesi içinde açılmalıdır. Bunun nedeni, UML diyagramının modelleme projesi tarafından sahip olunan bir modelin görünümünü göstereceğinden oluşur.

## <a name="NonModelDiagrams"></a>Modelleme projesi gerektirmeyen diyagramlar
 Aşağıdaki tür diyagramlar modelleme projesinin bir parçası değildir:

- Kaynak kodun görünümleri olarak oluşturulan sınıf diyagramları. Bunlar UML sınıf diyagramlarıyla ilgili değildir. Daha fazla bilgi için bkz. [sınıfları ve türleri tasarlama ve görüntüleme](../ide/designing-and-viewing-classes-and-types.md).

- Kod haritaları. Bkz: [Çözümlerinizdeki bağımlılıkları eşleme](../modeling/map-dependencies-across-your-solutions.md).

- UML diyagramları veya etki alanına özgü diller gibi katman diyagramları olmayan diyagramlar.

## <a name="TroubleshootingModelingProjects"></a>Modelleme projelerinde ve diyagramlarda sorun giderme
 Aşağıdaki tabloda, modelleme projelerinde veya diyagramlarında ve bunları nasıl çözebileceğinizi açıklayan sorunlar açıklanmaktadır:

|**Konuda**|**Mesine**|**Çözümleme**|
|---------------|----------------|--------------------|
|Modelleme projesi, çözüme açılamaz veya yüklenemez.<br /><br /> Aşağıdaki ileti görüntülenir:<br /><br /> "Çözümdeki bir veya daha fazla proje doğru şekilde yüklenmedi. Ayrıntılar için lütfen Çıkış Penceresi bakın. "<br /><br /> Çıkış penceresinde şu ileti görüntülenir:<br /><br /> "*ModelingProjectFilenameAndPath*. modelproj: hata: tanınmayan GUID biçimi."|Modelleme projesi aynı ada sahip ve aynı çözümde olan projelere başvuruları vardır.<br /><br /> Örneğin, bir katman aynı ada sahip ve aynı çözümde olan projelere bağlanır.|Modelleme Proje dosyasını açmak için bir metin düzenleyici kullanın, başvuruları kaldırın ve ardından modelleme projesini tekrar açmayı deneyin.<br /><br /> Bu sorundan kaçınmak için, aynı ada sahip projelere başvurular eklemeyin. Projelerin benzersiz adlara sahip olduğundan emin olun.|
|Diğer modelleme projelerine veya çözümdeki diğer konumlara eklenen, kopyalanmış veya sürüklenen diyagramlarda öğeler eksik.<br /><br /> veya<br /><br /> Bir diyagramı açmaya çalıştığınızda aşağıdaki iletiler görüntülenir:<br /><br /> -"Bu projede tanımları bulunmadığından, diyagramdaki bazı şekiller veya bağlayıcılar eksik. Diyagram kapalıyken tanımlar modelden silindi ya da diyagram bu tanımları içermeyen başka bir projeye kopyalandı. "<br /><br /> veya<br /><br /> -"Bu belge başka bir proje tarafından açılmış."|Diyagram dosyası, bir modelleme projesinden başka bir modelleme projesine veya çözümdeki başka bir konuma eklenmiş, sürüklenen veya kopyalanmış.|Bir diyagram dosyasını kopyalamak için yeni bir diyagram oluşturun ve sonra öğeleri kaynak diyagramından yeni diyagrama kopyalayın.|

## <a name="see-also"></a>Ayrıca Bkz.
 [Modelleme çözümünüzü](../modeling/structure-your-modeling-solution.md) [ve UML modellerini ve diyagramları düzenleme](../modeling/edit-uml-models-and-diagrams.md)
