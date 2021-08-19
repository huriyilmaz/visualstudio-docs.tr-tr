---
title: Şerit XML
description: Şerit (görsel Tasarımcı) öğesi tarafından desteklenmeyen bir şekilde özelleştirmek istiyorsanız şerit (XML) öğesini nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VSTO.Ribbon.RibbonXMLItem
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom Ribbon, XML
- customizing the Ribbon, XML
- Ribbon [Office development in Visual Studio], XML
- callback methods
- custom Ribbon, displaying
- custom Ribbon, defining behavior
- XML [Office development in Visual Studio], Ribbon
- customizing the Ribbon, defining behavior
- Ribbon [Office development in Visual Studio], customizing
- customizing the Ribbon, displaying
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 23172ee92923faab31a6b5c534076ddf067dc0a0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122155557"
---
# <a name="ribbon-xml"></a>Şerit XML
  Şerit (XML) öğesi, XML kullanarak bir şeridi özelleştirmenize olanak sağlar. Şeriti şerit (görsel Tasarımcı) öğesi tarafından desteklenmeyen bir şekilde özelleştirmek istiyorsanız şerit (XML) öğesini kullanın. Her öğe ile yapabileceklerinize ilişkin bir karşılaştırma için bkz. [Şerit 'e genel bakış](../vsto/Ribbon-overview.md).

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

## <a name="add-a-ribbon-xml-item-to-a-project"></a>Bir projeye Şerit (XML) öğesi ekleme
 **yeni öğe ekle** iletişim kutusundan herhangi bir Office projesine **şerit (XML)** öğesi ekleyebilirsiniz. Visual Studio, projenize otomatik olarak aşağıdaki dosyaları ekler:

- Şerit XML dosyası. Bu dosya, Şerit kullanıcı arabirimini (UI) tanımlar. Sekmeler, gruplar ve denetimler gibi kullanıcı arabirimi öğelerini eklemek için bu dosyayı kullanın. Ayrıntılar için bu konunun ilerleyen kısımlarında yer alarak [ŞERIT XML dosya başvurusu](#RibbonDescriptorFile) bölümüne bakın.

- Şerit kod dosyası. Bu dosya *Şerit sınıfını* içerir. Bu sınıf, **Yeni öğe Ekle** Iletişim kutusunda **Şerit (XML)** öğesi için belirttiğiniz ada sahiptir. Microsoft Office uygulamalar özel şeridi yüklemek için bu sınıfın bir örneğini kullanır. Ayrıntılar için bu konunun ilerleyen kısımlarında yer alarak [Ribbon Class Reference](#RibbonExtensionClass) bölümüne bakın.

  Varsayılan olarak, bu dosyalar Şeritteki **Eklentiler sekmesine özel bir grup ekler.**

## <a name="display-the-custom-ribbon-in-a-microsoft-office-application"></a>Microsoft Office uygulamasında özel şeridi görüntüleme
 projenize **şerit (XML)** öğesi ekledikten sonra, yöntemi geçersiz kılan ve şerit XML sınıfını Office uygulamasına döndüren **thisaddın**, **ThisWorkbook** veya **ThisDocument** sınıfına kod eklemeniz gerekir `CreateRibbonExtensibilityObject` .

 Aşağıdaki kod örneği, yöntemini geçersiz kılar `CreateRibbonExtensibilityObject` ve MyRibbon adlı bir ŞERIT XML sınıfı döndürür.

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs" id="Snippet1":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb" id="Snippet1":::

## <a name="define-the-behavior-of-the-custom-ribbon"></a>Özel şeridin davranışını tanımlama
 *Geri çağırma yöntemleri* oluşturarak Şeritteki bir düğmeye tıklanması gibi kullanıcı eylemlerine yanıt verebilirsiniz. geri çağırma yöntemleri Windows Forms denetimlerindeki olaylara benzer, ancak uı öğesinin XML dosyasındaki bir öznitelik tarafından tanımlanır. Yöntemleri şerit sınıfına yazdığınızda, bir denetim öznitelik değeriyle aynı ada sahip olan yöntemi çağırır. Örneğin, bir Kullanıcı Şeritteki bir düğmeye tıkladığında çağrılan bir geri çağırma yöntemi oluşturabilirsiniz. Bir geri çağırma yöntemi oluşturmak için iki adım gereklidir:

- Kodunuzda bir geri çağırma yöntemi tanımlayan Şerit XML dosyasındaki bir denetime öznitelik atayın.

- Şerit sınıfında geri çağırma yöntemini tanımlayın.

> [!NOTE]
> Outlook ek bir adım gerektirir. Daha fazla bilgi için bkz. [Outlook için bir şeridi özelleştirme](../vsto/customizing-a-ribbon-for-outlook.md).

 Bir uygulamayı şeritten nasıl otomatikleştirebileceğinizi gösteren bir anlatım için bkz. [Izlenecek yol: ŞERIT XML kullanarak özel sekme oluşturma](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md).

### <a name="assign-callback-methods-to-controls"></a>Denetimlere geri çağırma yöntemleri atama
 Şerit XML dosyasındaki bir denetime geri çağırma yöntemi atamak için, geri çağırma yönteminin türünü ve yöntemin adını belirten bir öznitelik ekleyin. Örneğin, aşağıdaki öğe adlı bir **OnAction** geri çağırma yöntemine sahip bir iki durumlu düğmeyi tanımlar `OnToggleButton1` .

```xml
<toggleButton id="toggleButton1" onAction="OnToggleButton1" />
```

 Kullanıcı belirli bir denetimle ilişkili ana görevi gerçekleştirdiğinde, **OnAction** çağrılır. Örneğin, Kullanıcı düğmeye tıkladığında iki durumlu düğmenin **OnAction** geri çağırma yöntemi çağırılır.

 Özniteliğinde belirttiğiniz yöntemi herhangi bir ada sahip olabilir. Ancak, Şerit kod dosyasında tanımladığınız yöntemin adıyla eşleşmesi gerekir.

 Şerit denetimlerine atayabileceğiniz birçok farklı türde geri arama yöntemi vardır. her denetim için kullanılabilen geri çağırma yöntemlerinin tüm listesi için bkz. [geliştiriciler için Office (2007) şerit kullanıcı arabirimini özelleştirme (3. kısım 3)](/previous-versions/office/developer/office-2007/aa722523(v=office.12))teknik makalesi.

### <a name="define-callback-methods"></a><a name="CallBackMethods"></a> Geri çağırma yöntemlerini tanımlama
 Şerit kod dosyasındaki Şerit sınıfında geri çağırma yöntemlerinizi tanımlayın. Bir geri çağırma yönteminde birkaç gereksinim vardır:

- Ortak olarak bildirilmelidir.

- Adının, Şerit XML dosyasındaki bir denetime atadığınız geri çağırma yönteminin adıyla eşleşmesi gerekir.

- İmzası, ilişkili şerit denetimi için kullanılabilen bir geri arama yöntemi türünün imzasıyla eşleşmelidir.

  şerit denetimleri için geri çağırma yöntemi imzalarının tüm listesi için bkz. [geliştiriciler için Office (2007) şerit kullanıcı arabirimini özelleştirme (3. kısım 3)](/previous-versions/office/developer/office-2007/aa722523(v=office.12))teknik makalesi. Visual Studio, şerit kod dosyasında oluşturduğunuz geri çağırma yöntemleri için ıntellisense desteği sağlamaz. Geçerli bir imzayla eşleşmeyen bir geri çağırma yöntemi oluşturursanız, kod derlenir, ancak Kullanıcı denetime tıkladığında hiçbir şey olmaz.

  Tüm geri çağırma yöntemlerinin <xref:Microsoft.Office.Core.IRibbonControl> , yöntemi çağıran denetimi temsil eden bir parametresi vardır. Bu parametreyi, birden fazla denetim için aynı geri çağırma yöntemini yeniden kullanmak için kullanabilirsiniz. Aşağıdaki kod örneğinde, kullanıcının tıkladığı denetime bağlı olarak farklı görevler gerçekleştiren bir **OnAction** geri çağırma yöntemi gösterilmektedir.

  :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_RibbonOutlookBasic/Ribbon1.cs" id="Snippet2":::
  :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_RibbonOutlookBasic/Ribbon1.vb" id="Snippet2":::

## <a name="ribbon-xml-file-reference"></a><a name="RibbonDescriptorFile"></a> Şerit XML dosyası başvurusu
 Şerit XML dosyasına öğeler ve öznitelikler ekleyerek özel şeritlerinizi tanımlayabilirsiniz. Varsayılan olarak, Şerit XML dosyası aşağıdaki XML 'i içerir.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<customUI xmlns="http://schemas.microsoft.com/office/2006/01/customui" onLoad="OnLoad">
  <ribbon>
    <tabs>
      <tab idMso="TabAddIns">
        <group id="MyGroup"
               label="My Group">
        </group>
      </tab>
    </tabs>
  </ribbon>
</customUI>
```

 Aşağıdaki tabloda, Şerit XML dosyasındaki varsayılan öğeler açıklanmaktadır.

|Öğe|Açıklama|
|-------------|-----------------|
|**Customuı**|VSTO eklentisi projesindeki özel şeridi temsil eder.|
|**şeridi**|Şeridi temsil eder.|
|**sıralanan**|Bir Şerit sekmeleri kümesini temsil eder.|
|**sekmesinde**|Tek bir şerit sekmesini temsil eder.|
|**grup**|Şerit sekmesindeki bir denetim grubunu temsil eder.|

 Bu öğelerin, özel şeridin görünümünü ve davranışını belirten öznitelikleri vardır. Aşağıdaki tabloda, Şerit XML dosyasındaki varsayılan öznitelikler açıklanmaktadır.

|Öznitelik|Üst öğe|Açıklama|
|---------------|--------------------|-----------------|
|**onLoad**|**Customuı**|Uygulama Şeriti yüklediğinde çağrılan bir yöntemi tanımlar.|
|**ıdmso**|**sekmesinde**|Şeritte görüntülenecek yerleşik bir sekmeyi tanımlar.|
|**id**|**grup**|Grubu tanımlar.|
|**etiketin**|**grup**|Grupta görüntülenen metni belirtir.|

 Şerit XML dosyasındaki varsayılan öğeler ve öznitelikler, kullanılabilen öğelerin ve özniteliklerin küçük bir alt kümesidir. kullanılabilir öğelerin ve özniteliklerin tüm listesi için bkz. [geliştiriciler için Office (2007) şerit kullanıcı arabirimini özelleştirme (bölüm 2/3)](/previous-versions/office/developer/office-2007/aa338199(v=office.12))teknik makalesi.

## <a name="ribbon-class-reference"></a><a name="RibbonExtensionClass"></a> Şerit sınıfı başvurusu
 Visual Studio şerit kodu dosyasında şerit sınıfını oluşturur. Şeritteki denetimlerin geri çağırma yöntemlerini bu sınıfa ekleyin. Bu sınıf, <xref:Microsoft.Office.Core.IRibbonExtensibility> arabirimini uygular.

 Aşağıdaki tabloda bu sınıftaki varsayılan yöntemler açıklanmıştır.

|Yöntem|Açıklama|
|------------|-----------------|
|`GetCustomUI`|Şerit XML dosyasının içeriğini döndürür. Microsoft Office uygulamalar, özel şeritlerinizin kullanıcı arabirimini tanımlayan bir XML dizesi almak için bu yöntemi çağırır. Bu yöntem yöntemini uygular <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> . **Note:** `GetCustomUI` yalnızca Şerit XML dosyasının içeriğini döndürmek için uygulanmalıdır; VSTO eklentisini başlatmak için kullanılmamalıdır.   Özellikle, uygulamanıza iletişim kutularını veya diğer pencereleri görüntülemeyi `GetCustomUI` denemeyebilirsiniz. Aksi takdirde, özel şerit düzgün çalışmayabilir. Eklentinizi başlatan kodu çalıştırmanız VSTO, kodu olay `ThisAddIn_Startup` işleyiciye ekleyin.|
|`OnLoad`|parametresini <xref:Microsoft.Office.Core.IRibbonControl> alana `Ribbon` atar. Microsoft Office uygulamaları özel şeridi yükleyemedikleri zaman bu yöntemi çağırtır. Özel şeridi dinamik olarak güncelleştirmek için bu alanı kullanabilirsiniz. Daha fazla bilgi için Geliştiriciler için Office [(2007) Şerit](/previous-versions/office/developer/office-2007/aa338202(v=office.12))kullanıcı arabirimini özelleştirme (Bölüm 1/ 3) teknik makalesine bakın.|
|`GetResourceText`|Şerit `GetCustomUI` XML dosyasının içeriğini almak için yöntemi tarafından çağrılır.|

## <a name="see-also"></a>Ayrıca bkz.
- [Şerit'e genel bakış](../vsto/ribbon-overview.md)
- [Adım adım kılavuz: Şerit XML kullanarak özel sekme oluşturma](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
- [Office Kullanıcı arabirimi özelleştirmesi](../vsto/office-ui-customization.md)
