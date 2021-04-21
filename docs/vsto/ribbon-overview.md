---
title: Şerite genel bakış
description: Şeridin, daha kolay bulması ve komutların şeritte denetimler olarak görünmesi için ilgili komutları düzenlemenin bir yolu olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- customizing the Ribbon, multiple Ribbons
- Ribbon [Office development in Visual Studio], about Ribbon
- toolbars [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], multiple Ribbons
- toolbars [Office development in Visual Studio]
- custom Ribbon, multiple Ribbons
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 8920c8a402b4566cf95bb74626171cca833d32de
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825556"
---
# <a name="ribbon-overview"></a>Şerite genel bakış
  Şerit, daha kolay bulabilmeniz için ilgili komutları düzenlemenin bir yoludur. Komutlar şeritte denetimler olarak görünür. Denetimler, bir uygulama penceresinin üst kenarındaki yatay bir şerit üzerinde *gruplar* halinde düzenlenir. İlgili gruplar sekmeler üzerinde düzenlenmiştir.

 Microsoft Office sisteminin önceki sürümlerindeki menüler ve araç çubukları kullanılarak erişilen özelliklerin çoğuna artık şerit kullanılarak erişilebilir. Daha fazla bilgi için, [2007 Microsoft Office sistemine yönelik kullanıcı arabirimine yönelik teknik makale geliştiricisine genel bakış](/previous-versions/office/developer/office-2007/aa338198(v=office.12))makalesine bakın.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

## <a name="customize-the-microsoft-office-ribbon"></a>Microsoft Office şeridini özelleştirme
 Şeriti özelleştirmek için aşağıdaki şerit öğelerinden birini Office projenize ekleyin:

- **Şerit (görsel Tasarımcı)**

- **Şerit (XML)**

  Örneğin, Excel şeridini özelleştirmek için Excel VSTO eklenti projesine bir şerit öğesi ekleyin.

### <a name="ribbon-visual-designer-item"></a>Şerit (görsel Tasarımcı) öğesi
 **Şerit (görsel Tasarımcı)** öğesi, özel bir şerit tasarlayıp geliştirmenizi kolaylaştıran gelişmiş araçlar sağlar. Şeriti aşağıdaki yollarla özelleştirmek için **Şerit (görsel Tasarımcı)** öğesini kullanın:

- Şerite özel veya yerleşik sekmeler ekleyin.

- Özel veya yerleşik bir sekmeye özel gruplar ekleyin.

  > [!NOTE]
  > Bir Microsoft Office uygulamasının şeridinde zaten bulunan yerleşik bir sekme veya grup vardır. Örneğin, **veri** sekmesi Excel 'deki yerleşik bir sekmedir. **Bağlantılar** grubu, **veri** sekmesindeki yerleşik bir gruptur.

- Özel bir gruba özel denetimler ekleyin.

- Backstage görünümüne özel denetimler ekleyin.

  Şerit **(görsel Tasarımcı)** öğesini kullanarak bir şeridi özelleştirme hakkında daha fazla bilgi için bkz. [Şerit Tasarımcısı](../vsto/ribbon-designer.md).

### <a name="ribbon-xml-item"></a>Şerit (XML) öğesi
 Şeriti **Şerit (görsel Tasarımcı)** öğesi tarafından desteklenmeyen bir şekilde özelleştirmek istiyorsanız **Şerit (XML)** öğesini kullanın. Şeriti aşağıdaki yollarla özelleştirmek için **Şerit (XML)** öğesini kullanın:

- Özel bir sekmeye veya yerleşik bir sekmeye *yerleşik* gruplar ekleyin.

- Özel bir gruba yerleşik denetimler ekleyin.

- Yerleşik denetimlerin olay işleyicilerini geçersiz kılmak için özel kod ekleyin.

- Hızlı erişim araç çubuğunu özelleştirin.

- Tam KIMLIK kullanarak VSTO eklentisi arasında bir Şerit özelleştirmesi paylaşabilirsiniz.

  Şerit **(XML)** öğesini kullanarak Şeriti özelleştirme hakkında daha fazla bilgi için bkz. [Ribbon XML](../vsto/ribbon-xml.md).

## <a name="export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>Şerit Tasarımcısından Şerit XML 'ine şerit aktarma
 Şerit Tasarımcısını kullanarak bir şerit oluşturursanız ve şerit **(görsel Tasarımcı)** öğesinin desteklemediği yollarla şeridi özelleştirmek istediğinize karar verirseniz, Şeriti XML 'e dışarı aktarabilirsiniz.

 Visual Studio otomatik olarak bir **Şerit (XML)** öğesi oluşturur ve Şerit XML dosyasını Şeritteki her denetim için öğeler ve öznitelikler ile doldurur.

 Şerit Tasarımcısı 'nın **Özellikler** penceresindeki özelliklerin hepsı Şerit XML dosyasına aktarılmaz.  Örneğin, Visual Studio **resim** veya **metin** özelliğinin değerini dışarı aktarmaz. Bunun nedeni, bir görüntü atamak veya bir denetimin metnini ayarlamak için, içe aktarılmış projenin Şerit kod dosyasında bir geri çağırma yöntemi oluşturmanız gerekir. Visual Studio, dışa aktarma işleminin bir parçası olarak otomatik olarak geri çağırma yöntemleri oluşturmaz.

 Ayrıca, değiştirilmemiş varsayılan özellik değerleri, sonuçta elde edilen Şerit XML dosyasında görünmez.

 Şeriti XML 'e aktarma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Şerit Tasarımcısından ŞERIT XML 'ine nasıl bir şerit dışarı aktarma](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md).

### <a name="update-the-code"></a>Kodu güncelleştirme
 **Çözüm Gezgini** yeni bir Şerit kod dosyası eklenir. Bu dosya Ribbon XML sınıfını içerir. `Ribbon Callbacks`Bir düğmeye tıklanması gibi kullanıcı eylemlerini işlemek için bu sınıfın bölgesinde geri çağırma yöntemleri oluşturmanız gerekir. Olay işleyicilerindeki kodunuzu bu geri çağırma yöntemlerine taşıyın ve şerit genişletilebilirliği (RibbonX) programlama modeliyle çalışmak için kodu değiştirin. Daha fazla bilgi için bkz. [ŞERIT XML](../vsto/ribbon-xml.md).

 Ayrıca `ThisAddIn` , `ThisWorkbook` yöntemi geçersiz kılan, veya sınıfına kod eklemeniz gerekir `ThisDocument` `CreateRibbonExtensibilityObject` ve Office uygulamasına Şerit XML sınıfını geri döndürür.

 Daha fazla bilgi için bkz. [ŞERIT XML](../vsto/ribbon-xml.md).

## <a name="add-multiple-ribbon-items-to-a-project"></a>Projeye birden çok şerit öğesi ekleme
 Tek bir projeye birden fazla şerit öğesi ekleyebilirsiniz. Aşağıdaki iki görevden birini gerçekleştirmek istiyorsanız bu yararlı olur:

- Outlook *Inspector* için şeritler oluşturun. Daha fazla bilgi için bkz. [Outlook için bir şeridi özelleştirme](../vsto/customizing-a-ribbon-for-outlook.md).

    > [!NOTE]
    > Inspector, kullanıcılar e-posta iletisi oluşturma gibi belirli görevleri gerçekleştirirken açılan bir penceredir.

- Çalışma zamanında görüntülenecek şeridi seçin.

### <a name="select-which-ribbons-to-display-at-run-time"></a>Çalışma zamanında görüntülenecek şeritleri seçin
 Bir proje birden fazla şerit içerebildiğinden, çalışma zamanında görüntülenecek Şeriti seçebilirsiniz.

 Çalışma zamanında görüntülenecek bir Şerit seçmek için, `CreateRibbonExtensibilityObject` projenizin, veya sınıfındaki yöntemini geçersiz kılın `ThisAddin` `ThisWorkbook` `ThisDocument` ve göstermek istediğiniz şeridi döndürün. Aşağıdaki örnek, adlı bir alanın değerini denetler `myCondition` ve uygun şeridi döndürür.

> [!NOTE]
> Bu örnekte kullanılan sözdizimi, **Şerit (görsel Tasarımcı)** öğesi kullanılarak oluşturulmuş bir şerit döndürüyor. **Şerit (XML)** öğesi kullanılarak oluşturulan bir şeridi döndürme için sözdizimi biraz farklıdır. **Şerit (XML)** öğesi döndürme hakkında daha fazla bilgi için bkz. [Ribbon XML](../vsto/ribbon-xml.md).

 Şu kodu ekleyin:

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_Ribbon_choose_Ribbon_4/ThisWorkbook.vb" id="Snippet1":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_Ribbon_choose_Ribbon_4/ThisWorkbook.cs" id="Snippet1":::

### <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Nasıl yapılır: Şeriti özelleştirmeye başlama](../vsto/how-to-get-started-customizing-the-ribbon.md)|Bir Microsoft Office uygulamasının şeritlerini özelleştirmeyi, bir **Şerit (görsel Tasarımcı)** veya **Şerit (XML)** öğesini bir Office projesine eklemeyi gösterir.|
|[Şerit Tasarımcısı](../vsto/ribbon-designer.md)|Bir Microsoft Office uygulamasının şeritlerine özel sekmeler, gruplar ve denetimler eklemek için şerit tasarımcısını nasıl kullanabileceğinizi açıklar.|
|[İzlenecek yol: Şerit Tasarımcısını kullanarak özel sekme oluşturma](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)|Şerit Tasarımcısını kullanarak özel bir şerit sekmesi oluşturmayı gösterir. Özel sekmeye denetim eklemek ve bunları konumlandırmak için şerit tasarımcısını kullanabilirsiniz.|
|[Şerit nesne modeline genel bakış](../vsto/ribbon-object-model-overview.md)|Çalışma zamanında Şerit denetimlerinin özelliklerini almak ve ayarlamak için kullanabileceğiniz, türü kesin belirlenmiş nesne modeline genel bir bakış sağlar.|
|[İzlenecek yol: çalışma zamanında Şeritteki denetimleri güncelleştirme](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)|Şerit 'i Office uygulamasına yükledikten sonra Şeritteki denetimleri güncelleştirmek için şerit nesne modelinin nasıl kullanılacağını gösterir.|
|[Outlook için şerit özelleştirme](../vsto/customizing-a-ribbon-for-outlook.md)|Microsoft Office Outlook 'ta şeridi özelleştirmeye yönelik rehberlik sağlar.|
|[InfoPath için bir şeridi özelleştirme](../vsto/customizing-a-ribbon-for-infopath.md)|Microsoft Office InfoPath 'te Şeriti özelleştirmeye yönelik rehberlik sağlar.|
|[Çalışma zamanında Şerite erişin](../vsto/accessing-the-ribbon-at-run-time.md)|Şerit 'in nasıl gösterileceğini, gizleneceğini ve değiştirileceğini gösterir ve kullanıcıların kodu özel bir görev bölmesinde, Eylemler bölmesinde veya Outlook form bölgesindeki denetimlerden çalıştırmasına olanak tanır.|
|[Nasıl yapılır: Şeritteki sekmenin konumunu değiştirme](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)|Şeritteki sekmelerin sırasının nasıl değiştirileceğini gösterir.|
|[Nasıl yapılır: yerleşik bir sekmeyi özelleştirme](../vsto/how-to-customize-a-built-in-tab.md)|Yerleşik bir sekmeye grupların ve denetimlerin nasıl ekleneceğini gösterir.|
|[Nasıl yapılır: Backstage görünümüne denetimler ekleme](../vsto/how-to-add-controls-to-the-backstage-view.md)|**Dosyaya** tıkladığınızda açılan menüye denetimlerin nasıl ekleneceğini gösterir.|
|[Nasıl yapılır: Şerit grubuna iletişim kutusu Başlatıcısı Ekleme](../vsto/how-to-add-a-dialog-box-launcher-to-a-ribbon-group.md)|Şeritteki herhangi bir gruba bir iletişim kutusu Başlatıcısı ekleneceğini gösterir.|
|[Nasıl yapılır: Şerit Tasarımcısından Şerit XML 'ine şerit aktarma](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)|Şeriti tasarımcıdan Şerit XML 'ine dışa aktararak, şeridin gelişmiş yollarla nasıl özelleştirileceğini gösterir.|
|[Şerit XML](../vsto/ribbon-xml.md)|Şerit XML kullanarak bir şeridi nasıl özelleştirebileceğinizi açıklar.|
|[İzlenecek yol: Şerit Tasarımcısını kullanarak özel sekme oluşturma](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)|**Şerit (XML)** öğesini kullanarak nasıl özel Şerit sekmesinin oluşturulduğunu gösterir.|
