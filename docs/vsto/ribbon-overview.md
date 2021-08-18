---
title: Şerit'e genel bakış
description: Şeridin, ilgili komutları daha kolay bulunacak şekilde düzenlemenin ve komutların şeritte denetim olarak nasıl görüntüleyeceklerini öğrenin.
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 2f125edbf25c5a7732f3ce168bf96b90f4d94c11
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122099522"
---
# <a name="ribbon-overview"></a>Şerit'e genel bakış
  Şerit, ilgili komutları daha kolay bulunacak şekilde düzenlemenin bir yolu olarak kullanılır. Komutlar şeritte denetim olarak görünür. Denetimler, uygulama *penceresinin* üst kenarında yatay şerit üzerinde gruplar halinde düzenlenmiştir. İlgili gruplar sekmelerde düzenlenmiştir.

 Microsoft Office sisteminin önceki sürümlerinde menüler ve araç çubukları kullanılarak erişilen özelliklerin çoğuna artık şerit kullanılarak erişilebilir. Daha fazla bilgi için, [2007 ve 2007](/previous-versions/office/developer/office-2007/aa338198(v=office.12))işletim sistemi için kullanıcı arabirimine geliştirici genel Microsoft Office bakın.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

## <a name="customize-the-microsoft-office-ribbon"></a>Microsoft Office Şeridini Özelleştirme
 Şeridi özelleştirmek için Office projenize aşağıdaki Şerit öğeleri Office ekleyin:

- **Şerit (Görsel Tasarımcı)**

- **Şerit (XML)**

  Örneğin, Excel Şeridini özelleştirmek için, bir Excel VSTO Eklenti projesine Şerit öğesi ekleyin.

### <a name="ribbon-visual-designer-item"></a>Şerit (Görsel Tasarımcı) öğesi
 Şerit **(Görsel Tasarımcı)** öğesi, özel şerit tasarlamanızı ve geliştirmenizi kolaylaştıran gelişmiş araçlar sağlar. Şeridi aşağıdaki yollarla özelleştirmek için Şerit **(Görsel Tasarımcı)** öğesini kullanın:

- Şerite özel veya yerleşik sekmeler ekleyin.

- Özel veya yerleşik bir sekmeye özel gruplar ekleyin.

  > [!NOTE]
  > Yerleşik sekme veya grup, bir uygulamanın şeridinde zaten mevcut Microsoft Office olur. Örneğin Veri **sekmesi,** veri sekmesindeki yerleşik bir Excel. Bağlantılar  grubu, Veri sekmesindeki yerleşik bir **gruptur.**

- Özel bir gruba özel denetimler ekleyin.

- Backstage Görünümüne özel denetimler ekleyin.

  Şerit **(Görsel Tasarımcı)** öğesini kullanarak bir şeridi özelleştirme hakkında daha fazla bilgi için bkz. [Şerit tasarımcısı.](../vsto/ribbon-designer.md)

### <a name="ribbon-xml-item"></a>Şerit (XML) öğesi
 Şeridi **Şerit (Görsel Tasarımcı)** öğesi tarafından desteklenmiyor bir şekilde özelleştirmek için **Şerit (XML) öğesini** kullanın. Şeridi aşağıdaki yollarla özelleştirmek için Şerit **(XML)** öğesini kullanın:

- Özel *bir sekmeye* veya yerleşik sekmeye yerleşik gruplar ekleyin.

- Özel bir gruba yerleşik denetimler ekleyin.

- Yerleşik denetimlerin olay işleyicilerini geçersiz kılmak için özel kod ekleyin.

- Hızlı Erişim Araç Çubuğunu özelleştirin.

- Tam kimlik kullanarak VSTO Arasında Şerit özelleştirmesi paylaşın.

  Şerit **(XML)** öğesini kullanarak şeridi özelleştirme hakkında daha fazla bilgi için bkz. [Şerit XML](../vsto/ribbon-xml.md).

## <a name="export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>Şerit Tasarımcısı'nda şeridi Şerit XML'e dışarı aktarma
 Şerit Tasarımcısı'ı kullanarak bir şerit oluşturduktan sonra şeridi Şerit **(Görsel Tasarımcı)** öğesinin desteklemey yollarında özelleştirmek istediğinize karar verdiyebilirsiniz. Şeridi XML'ye aktarabilirsiniz.

 Visual Studio bir **Şerit (XML)** öğesi oluşturur ve Şerit XML dosyasını şeritteki her denetim için öğeler ve özniteliklerle doldurmak için kullanılır.

 Şerit Tasarımcısı'nın Özellikler **penceresindeki** özelliklerin hepsi Şerit XML dosyasına aktarlanmaz.  Örneğin, Visual Studio Image veya Text özelliğinin **değerini dışarı** **aktarmaz.** Bunun nedeni, dışarı aktardığınız projenin Şerit kod dosyasında görüntü atamak veya denetimin metnini ayarlamak için bir geri çağırma yöntemi oluşturmanız olmasıdır. Visual Studio, dışarı aktarma işleminin bir parçası olarak otomatik olarak geri çağırma yöntemleri oluşturmaz.

 Ayrıca, değişmeyen varsayılan özellik değerleri, sonuçta elde edilen Şerit XML dosyasında görünmez.

 Şeridi XML'e aktarma hakkında daha fazla bilgi için bkz. Nasıl kullanılır: Şerit Tasarımcısından [Şerit XML'e şerit aktarma.](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)

### <a name="update-the-code"></a>Kodu güncelleştirme
 dosyasına yeni bir Şerit kod dosyası **Çözüm Gezgini.** Bu dosya, Ribbon XML sınıfını içerir. Bir düğmeye tıklama gibi kullanıcı eylemlerini işlemek için bu sınıfın `Ribbon Callbacks` bölgesinde geri çağırma yöntemleri oluşturmanız gerekir. Kodunuzu olay işleyicilerinden bu geri çağırma yöntemlerine taşıma ve Kodu Şerit genişletilebilirliği (RibbonX) programlama modeliyle çalışacak şekilde değiştirme. Daha fazla bilgi için bkz. [Şerit XML](../vsto/ribbon-xml.md).

 Ayrıca yöntemini geçersiz karak Şerit XML sınıfını uygulamanıza döndüren , veya `ThisAddIn` `ThisWorkbook` `ThisDocument` `CreateRibbonExtensibilityObject` sınıfına kod Office gerekir.

 Daha fazla bilgi için bkz. [Şerit XML](../vsto/ribbon-xml.md).

## <a name="add-multiple-ribbon-items-to-a-project"></a>Projeye birden çok Şerit öğe ekleme
 Tek bir projeye birden fazla Şerit öğesi eklemek için kullanabilirsiniz. Bu, aşağıdaki iki görevden birini gerçekleştirmek istediğinizde kullanışlıdır:

- Outlook *Inspectors için şeritler oluşturun.* Daha fazla bilgi için [bkz. Bir şeridi Outlook.](../vsto/customizing-a-ribbon-for-outlook.md)

    > [!NOTE]
    > Denetçi, kullanıcılar e-posta iletisi oluşturma gibi belirli görevleri gerçekleştirecekleri zaman açılan bir penceredir.

- Çalışma zamanında hangi şeridin görüntüleniyor olduğunu seçin.

### <a name="select-which-ribbons-to-display-at-run-time"></a>Çalışma zamanında hangi şeritlerin görüntüleniyor olduğunu seçin
 Bir proje birden fazla şerit içereye sahip olduğundan, çalışma zamanında hangi şeridin görüntülen bir şerit olduğunu seçin.

 Çalışma zamanında görüntülemek üzere bir şerit seçmek için projenizin , veya sınıfındaki yöntemini geçersiz kılın ve görüntülemek `CreateRibbonExtensibilityObject` `ThisAddin` istediğiniz şeridi geri `ThisWorkbook` `ThisDocument` çalıştırın. Aşağıdaki örnek adlı bir alanın değerini denetler `myCondition` ve uygun şeridi döndürür.

> [!NOTE]
> Bu örnekte kullanılan söz dizimi, Şerit **(Görsel Tasarımcı)** öğesi kullanılarak oluşturulmuş bir şerit döndürür. Şerit **(XML)** öğesi kullanılarak oluşturulan bir şeridi döndüren söz dizimi biraz farklıdır. Şerit **(XML)** öğesi iade hakkında daha fazla bilgi için bkz. [Şerit XML](../vsto/ribbon-xml.md).

 Şu kodu ekleyin:

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_Ribbon_choose_Ribbon_4/ThisWorkbook.vb" id="Snippet1":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_Ribbon_choose_Ribbon_4/ThisWorkbook.cs" id="Snippet1":::

### <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Nasıl Kullanmaya başlayın: şeridi özelleştirme](../vsto/how-to-get-started-customizing-the-ribbon.md)|Bir uygulamanın şeridini özelleştirme, Microsoft Office projesine **Şerit (Görsel Tasarımcı)** veya **Şerit (XML)** Office gösterir.|
|[Şerit tasarımcısı](../vsto/ribbon-designer.md)|Bir uygulamanın şeridine özel sekmeler, gruplar ve denetimler eklemek için Şerit Tasarımcısı'Microsoft Office açıklar.|
|[Adım adım kılavuz: Şerit Tasarımcısını kullanarak özel sekme oluşturma](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)|Şerit Tasarımcısı'nın kullanarak özel şerit sekmesinin nasıl oluşturul olduğunu gösterir. Özel sekmede denetim eklemek ve konumlandırmak için Şerit Tasarımcısı'nın kullanabilirsiniz.|
|[Şerit nesne modeline genel bakış](../vsto/ribbon-object-model-overview.md)|Çalışma zamanında Şerit denetimlerinin özelliklerini almak ve ayarlamak için kullanabileceğiniz türü kesin olarak ayarlanmış nesne modeline genel bir bakış sağlar.|
|[Adım adım kılavuz: Çalışma zamanında şeritteki denetimleri güncelleştirme](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)|Şerit uygulama içine yüklendikten sonra şeritteki denetimleri güncelleştirmek için Şerit nesne modelinin nasıl Office gösterir.|
|[Bir şeridi Outlook](../vsto/customizing-a-ribbon-for-outlook.md)|Çalışma sayfalarında şeridi özelleştirmeye yönelik Microsoft Office Outlook.|
|[InfoPath için şerit özelleştirme](../vsto/customizing-a-ribbon-for-infopath.md)|InfoPath'te şeridi özelleştirmeye Microsoft Office sağlar.|
|[Çalışma zamanında şerite erişme](../vsto/accessing-the-ribbon-at-run-time.md)|Şeridi göstermeyi, gizlemeyi ve değiştirmeyi ve kullanıcıların özel bir görev bölmesinde, eylemler bölmesinde veya form bölgesinde denetimlerden kodu Outlook gösterir.|
|[Nasıl yapın: Şeritteki bir sekmenin konumunu değiştirme](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)|Şeritteki sekmelerin sıralamalarını değiştirmeyi gösterir.|
|[Nasıl yapılır: Yerleşik sekmeyi özelleştirme](../vsto/how-to-customize-a-built-in-tab.md)|Yerleşik sekmeye grup ve denetim eklemeyi gösterir.|
|[Nasıl olur: Backstage Görünümüne denetimler ekleme](../vsto/how-to-add-controls-to-the-backstage-view.md)|Dosya'ya tıklarsanız açılan menüye denetimler eklemeyi **gösterir.**|
|[Nasıllı: Şerit grubuna iletişim kutusu başlatıcısı ekleme](../vsto/how-to-add-a-dialog-box-launcher-to-a-ribbon-group.md)|Şeritteki herhangi bir gruba iletişim kutusu başlatıcısı eklemek için gösterir.|
|[Nasıl kullanılır: Şerit Tasarımcısı'nda şeritten Şerit XML'sini dışarı aktarma](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)|Şeridi tasarımcıdan Şerit XML'e aktararak şeridi gelişmiş yollarla özelleştirmeyi gösterir.|
|[Şerit XML](../vsto/ribbon-xml.md)|Şerit XML kullanarak bir şeridi nasıl özelleştirebileceğinizi açıklar.|
|[Adım adım kılavuz: Şerit Tasarımcısını kullanarak özel sekme oluşturma](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)|Şerit (XML) öğesini kullanarak özel Şerit **sekmesinin nasıl oluşturulabileceklerini** gösterir.|
