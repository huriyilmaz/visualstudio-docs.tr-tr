---
title: Kod yazma Office yazma
description: Farklı çözümlerde kod yazmayı Microsoft Office nesne modellerinin yönetilen koda nasıl Office hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.Project.RefactoringCancelled
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], writing code
- managed code [Office development in Visual Studio]
- Office development in Visual Studio, programming languages supported
- Office applications [Office development in Visual Studio], automating
- Office applications [Office development in Visual Studio], writing code
- writing code for Office solutions
- programming [Office development in Visual Studio], model
- Automation [Office development in Visual Studio], managed code
- application development [Office development in Visual Studio], programming model
- Office solutions [Office development in Visual Studio], writing code
- automating Office applications
- application development [Office development in Visual Studio], writing code
- application development [Office development in Visual Studio], automating
- Office projects [Office development in Visual Studio], changing namespaces
- solutions [Office development in Visual Studio], programming model
- programming [Office development in Visual Studio]
- namespaces [Office developmentin Visual Studio], changing in Office solutions
- projects [Office development in Visual Studio], writing code
- Office applications [Office development in Visual Studio], programming model
- managed code extensions [Office development in Visual Studio], writing code
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: d3029e58adaba6999d178a3be10f276c9ff21f14
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122135409"
---
# <a name="write-code-in-office-solutions"></a>Kod yazma Office yazma
  Kod yazmanın bazı yönleri Office projelerde yer alan diğer proje türlerinden farklı Visual Studio. Bu farkların çoğu, nesne modellerinin yönetilen Office nasıl ortaya çıkar? ile ilgilidir. Diğer farklar, projelerin tasarımıyla Office vardır.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="managed-code-and-office-programming"></a>Yönetilen kod ve Office programlama
 Tümleşik bir Microsoft Office çözümü oluşturmayı mümkün kılan temel teknoloji, Bileşen Nesne Modeli (COM) teknolojisinin bir parçası olan Otomasyon'dür. Otomasyon, uygun program arabirimlerini destekleyen herhangi bir uygulama, DLL veya ActiveX tarafından ortaya çıkan yazılım nesnelerini oluşturmak ve kontrol etmek için kod kullanmanızı sağlar.

### <a name="understand-primary-interop-assemblies"></a>Birincil birlikte çalışma derlemelerini anlama
 Microsoft Office uygulamaları işlevlerinin büyük bir fazlasını Otomasyon'da ortaya çıkarır. Ancak, yönetilen uygulamaları otomatikleştirmek için yönetilen Visual Basic (Visual Basic veya C# gibi) Office kullanılamaz. Yönetilen kod Office uygulamaları otomatikleştirmek için birincil birlikte çalışma derlemelerini (PIA Office birlikte çalışma derlemelerini kullansanız gerekir. Birincil birlikte çalışma derlemeleri, yönetilen kodun yönetilen uygulamaların COM tabanlı nesne modeliyle etkileşim Office sağlar.

 Her Microsoft Office uygulamanın PIA'sı vardır. Bir Office projesini Visual Studio, projeye otomatik olarak uygun PIA başvurusu eklenir. Projedeki diğer Office özelliklerini otomatikleştirmek için, uygun PIA'ya el ile bir başvuru eklemeniz gerekir. Daha fazla bilgi için [bkz. Nasıl Office derlemeleri aracılığıyla uygulamaları hedefle.](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)

### <a name="use-primary-interop-assemblies-at-design-time-and-runtime"></a>Tasarım zamanında ve çalışma zamanında birincil birlikte çalışma derlemelerini kullanma
 Geliştirme görevlerinin çoğunu Office için geliştirme bilgisayarınızda genel derleme önbelleğinde yüklü ve kayıtlı olan genel PIA'ların olması gerekir. Daha fazla bilgi için, [bkz. Configure a computer to develop Office .](../vsto/configuring-a-computer-to-develop-office-solutions.md)

 Veya Office hedef çözümlerini çalıştırmak için son kullanıcı bilgisayarlarında Office PIA'lar [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] gerekli değildir. Daha fazla bilgi için, [bkz. Tasarım ve Office çözümleri.](../vsto/designing-and-creating-office-solutions.md)

### <a name="use-types-in-primary-interop-assemblies"></a>Birincil birlikte çalışma derlemelerinde türleri kullanma
 Bu Office PIA'ları, Office uygulamalarının nesne modelini ortaya çıkaran türlerin ve doğrudan kodunuzda kullanılmak üzere amaçlanan ek altyapı türlerinin bir bileşimini içerir. Yazılım PIA'larında türlerine genel Office için, birincil birlikte çalışma derlemeleri içindeki [sınıflara ve arabirimlere genel Office bakın.](/previous-versions/office/office-12/ms247299\(v\=office.12\))

 Office PIA'lar, COM tabanlı nesne modellerinde türlere karşılık geldiği için, bu türleri kullanma şekliniz genellikle diğer yönetilen türlerden farklıdır. Örneğin, birincil birlikte çalışma derlemesinde isteğe bağlı Office yöntemleri çağırma yönteminiz, projeniz için kullandığınız programlama diline bağlıdır. Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:

- [çözümlerinde isteğe Office parametreleri.](../vsto/optional-parameters-in-office-solutions.md)

- [Çözümlerde Office bağlama.](../vsto/late-binding-in-office-solutions.md)

## <a name="program-model-of-office-projects"></a>Office projelerinin program modeli
 Tüm Office, kodunuz için giriş noktası sağlayan bir veya daha fazla oluşturulan sınıf içerir. Bu sınıflar ayrıca konak uygulamanın nesne modeline erişim ve eylem bölmeleri ve özel görev bölmeleri gibi özelliklere erişim sağlar.

### <a name="understand-the-generated-classes"></a>Oluşturulan sınıfları anlama
 Excel ve Word için belge düzeyi projelerinde, oluşturulan sınıf uygulamanın nesne modelinde üst düzey bir nesneye benzer. Örneğin, Word belge `ThisDocument` projesinde oluşturulan sınıf, Word nesne modelinde <xref:Microsoft.Office.Interop.Word.Document> sınıfıyla aynı üyeleri sağlar. Belge düzeyi projelerinde oluşturulan sınıflar hakkında daha fazla bilgi için [bkz. Program belge düzeyi özelleştirmeleri.](../vsto/programming-document-level-customizations.md)

 VSTO Eklenti projeleri adlı oluşturulan bir sınıf `ThisAddIn` sağlar. Bu sınıf, konak uygulamanın nesne modelinde bir sınıfa benzememektedir. Bunun yerine, bu sınıf VSTO eklentiyi temsil eder ve konak uygulamanın nesne modeline erişmek için kullanabileceğiniz üyeler sağlar ve VSTO eklentileri için kullanılabilir diğer özelliklere erişebilirsiniz. Daha fazla bilgi için [bkz. Program VSTO Eklentileri.](../vsto/programming-vsto-add-ins.md)

 Projelerde oluşturulan tüm sınıflar Office ve `Startup` olay `Shutdown` işleyicileri içerir. Kod yazmaya başlamanız için genellikle bu olay işleyicilere kod eklersiniz. Eklentinizi VSTO için olay işleyiciye kod `Startup` ekebilirsiniz. Eklentiniz tarafından kullanılan kaynakları VSTO için olay işleyiciye kod `Shutdown` ebilirsiniz. Daha fazla bilgi için [bkz. Office projelerinde olaylar.](../vsto/events-in-office-projects.md)

### <a name="access-the-generated-classes-at-run-time"></a>Oluşturulan sınıflara çalışma zamanında erişme
 Bir Office çözümü yüklendiğinde, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] projeniz içinde oluşturulan sınıfların her biri örneği oluşturulur. sınıfını kullanarak projenizin herhangi bir kodundan bu nesnelere `Globals` erişebilirsiniz. Örneğin, sınıfını kullanarak bir Şerit düğmesinin bir olay işleyicisi olan sınıfındaki kodu çağırabilir ve `Globals` `ThisAddIn` VSTO çağırabilirsiniz.

 Daha fazla bilgi için [bkz. Office projelerinde nesnelere genel erişim.](../vsto/global-access-to-objects-in-office-projects.md)

### <a name="namespace-considerations-in-office-solutions"></a>Office çözümlerde ad Office dikkat edilmesi gerekenler
 Projeyi oluşturdukktan *sonra bir Office* *projesinde* varsayılan ad alanını (veya Visual Basic ad alanını) değiştiremezsiniz. Varsayılan ad alanı her zaman projeyi oluşturulduğunda belirttiğiniz proje adıyla eşler. Projenizi yeniden adlandırdısanız varsayılan ad alanı değişmez. Projelerde varsayılan ad alanı hakkında daha fazla bilgi için [bkz. Uygulama Sayfası, Project Tasarımcısı &#40;C&#35;&#41;](../ide/reference/application-page-project-designer-csharp.md) ve Uygulama [Sayfası, Project Tasarımcısı &#40;Visual Basic&#41;. ](../ide/reference/application-page-project-designer-visual-basic.md)

### <a name="change-the-namespace-of-host-item-classes-in-c-projects"></a>C# projelerinde konak öğesi sınıflarının ad alanını değiştirme
 Konak öğesi sınıflarının (örneğin, `ThisAddIn` , `ThisWorkbook` veya sınıfları) Visual C# ve projelerinde kendi `ThisDocument` ad Office vardır. Varsayılan olarak, projenizin konak öğelerinin ad alanı, projeyi oluşturulduğunda belirttiğiniz proje adıyla eşler.

 Visual C# Office projesinde konak öğelerinin ad alanını değiştirmek için, Konak Öğesi için **Ad Alanı özelliğini** kullanın. Daha fazla bilgi için [bkz. Office projelerinde özellikler.](../vsto/properties-in-office-projects.md)

## <a name="supported-programming-languages-in-office-projects"></a>Office projelerinde desteklenen programlama dilleri
 Office proje şablonları yalnızca Visual Studio ve Visual C# Visual Basic dillerini destekler. Bu nedenle, bu proje şablonları yalnızca **Visual Basic** Yeni Project iletişim kutusunun **Visual C#** **düğümleri** altında [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] kullanılabilir. Daha fazla bilgi için, [bkz. How to: Create Office projects in Visual Studio.](../vsto/how-to-create-office-projects-in-visual-studio.md)

## <a name="language-choice-and-office-programming"></a>Dil seçimi ve Office programlama
 Microsoft Office özelleştirme Visual Basic for Applications (VBA) birlikte çalışmak için geliştirilmiştir. Visual Basic bazı gelişmeler devralındı. Örneğin, Visual Basic, isteğe bağlı parametreleri destekler. Başka bir ifadeyle, birincil birlikte çalışma derlemelerinde bazı yöntemleri çağırarak Visual C# Microsoft Office daha az kod yazabilirsiniz.

## <a name="program-with-visual-basic-vs-visual-c-in-office-solutions"></a>Visual Basic çözümlerde Visual C# ile Office program
 Visual C# Office kullanarak Visual Basic çözümleri oluşturabilirsiniz. Bu Microsoft Office modelleri Microsoft Visual Basic for Applications (VBA) ile birlikte kullanılacak şekilde tasarlanmalarına neden olduğundan, Visual Basic geliştiriciler Microsoft Office tarafından ortaya çıkar. Visual C# geliştiricileri, diğer geliştiricilerle Visual Basic çoğunu kullanabilir, ancak bazı durumlarda, Office nesne modellerini kullanmak için ek kod yazmaları gerekir. Ayrıca, geliştirme aşamasındaki temel programlama özellikleri ile Office C# dilinde yazılmış yönetilen kodlar arasında Visual Basic farklar vardır.

<!-- markdownlint-disable MD003 MD020 -->
## <a name="key-differences-between-visual-basic-and-visual-c"></a>Visual Basic Visual C arasındaki temel farklar #
<!-- markdownlint-enable MD003 MD020 -->

Aşağıdaki tabloda, geliştirme aşamasında Visual Basic Visual C# ile Office farklar yer alır.

|Özellik|Açıklama|Visual Basic desteği|Visual C# desteği|
|-------------|-----------------|--------------------------|------------------------|
|İsteğe bağlı parametreler|Birçok Microsoft Office yöntemi, yöntemini çağırarak gerekli olan parametrelere sahip olur. parametresi için bir değer geçirilse varsayılan değer kullanılır.|Visual Basic isteğe bağlı parametreleri destekler.|Visual C# çoğu durumda isteğe bağlı parametreleri destekler. Daha fazla bilgi için bkz. [Çözümlerde isteğe Office.](../vsto/optional-parameters-in-office-solutions.md)|
|Başvuruya göre parametreleri geçirme|Birincil birlikte çalışma derlemelerinin çoğunda Microsoft Office isteğe bağlı parametreler değere göre geçir olabilir. Ancak, bazı birincil birlikte çalışma derlemelerinde, başvuru türlerini kabul eden isteğe bağlı parametreler başvuruyla geçir gerekir.<br /><br /> Değer ve başvuru türü parametreleri hakkında daha fazla bilgi için bkz. Bağımsız değişkenleri değere göre ve başvuru [değerlerine göre &#40;Visual Basic&#41;](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference) (Visual Basic için) ve Parametreleri &#40;[C&#35; programlama kılavuzuna&#41;. ](/dotnet/csharp/programming-guide/classes-and-structs/passing-parameters)|Başvuruya göre parametrelerin geçmesi için ek bir çalışma gerekmez. Visual Basic derleyici gerektiğinde parametreleri başvuruya göre otomatik olarak iletir.|Çoğu durumda Visual C# derleyicisi gerektiğinde parametreleri başvuruya göre otomatik olarak iletir. Daha fazla bilgi için bkz. [Çözümlerde isteğe Office.](../vsto/optional-parameters-in-office-solutions.md)|
|Parametreli özellikler|Bazı özellikler parametreleri kabul eder ve salt okunur işlevler olarak davranır.|Visual Basic, parametreleri kabul eden özellikleri destekler.|Visual C# parametreleri kabul eden özellikleri destekler.|
|Geç bağlama|Geç bağlama, tasarım zamanında nesne türüne değişken atama yerine çalışma zamanında nesnelerin özelliklerini belirlemeyi içerir.|Visual Basic, Option Strict kapalı **olduğunda gecikmeli bağlama** gerçekleştirir. Option **Strict açık** olduğunda, nesneleri açıkça dönüştürmeniz ve geç bağlanmış üyelere erişmek için ad alanı türlerini <xref:System.Reflection> kullansanız gerekir. Daha fazla bilgi için [bkz. Çözümlerde Office bağlama.](../vsto/late-binding-in-office-solutions.md)|Visual C# hedefi olan projelerde geç bağlama [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] gerçekleştirir. Daha fazla bilgi için [bkz. Çözümlerde Office bağlama.](../vsto/late-binding-in-office-solutions.md)|

## <a name="key-differences-between-office-development-and-managed-code"></a>Geliştirme ve Office arasındaki temel farklar
 Aşağıdaki tabloda, Office veya Visual C# ile Visual Basic kod arasındaki temel farklar yer alır.

|Özellik|Açıklama|Visual Basic ve Visual C# desteği|
|-------------|-----------------|-----------------------------------------|
|Dizi dizinleri|Uygulama uygulamalarında koleksiyonların alt Microsoft Office 1 ile başlar. Visual Basic ve Visual C# 0 tabanlı diziler kullanır. Daha fazla bilgi için, [bkz. &#40;C&#35; programlama kılavuzu&#41;](/dotnet/csharp/programming-guide/arrays/index) [dizileri ve Visual Basic.](/dotnet/visual-basic/programming-guide/language-features/arrays/index)|Bir uygulamanın nesne modelinde bir koleksiyonun ilk öğesine erişmek Microsoft Office 0 yerine dizin 1'i kullanın.|

## <a name="see-also"></a>Ayrıca bkz.

- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
- [Office projelerinde nesnelere genel erişim](../vsto/global-access-to-objects-in-office-projects.md)
- [Office projelerinde olaylar](../vsto/events-in-office-projects.md)
- [Nasıl kullanılır: Birincil Office derlemeleri aracılığıyla uygulamaları hedefle](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)
- [Nasıl Office: Projelerde olay Office oluşturma](../vsto/how-to-create-event-handlers-in-office-projects.md)
- [Çözümlerde Office bağlama](../vsto/late-binding-in-office-solutions.md)
- [İşbirlikçi Office geliştirme](../vsto/collaborative-development-of-office-solutions.md)
