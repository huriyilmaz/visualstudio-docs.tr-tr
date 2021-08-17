---
title: Diğer VSTO çözümlerinden eklentilerde kod Office çağırma
description: Bir nesneyi, diğer VSTO çözümleri de dahil olmak üzere diğer çözümlere eklenti olarak nasıl Microsoft Office öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VBA [Office development in Visual Studio], calling code in application-level add-ins
- application-level add-ins [Office development in Visual Studio], calling code from other solutions
- calling add-in code
- add-ins [Office development in Visual Studio], calling code from other solutions
- interoperability [Office development in Visual Studio]
- calling code from VBA
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 428cf3cdb569eb8db0edde63728e27b736ad72a44488b009fdca000107709b62
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121424599"
---
# <a name="call-code-in-vsto-add-ins-from-other-office-solutions"></a>Diğer VSTO çözümlerinden eklentilerde kod Office çağırma
  Bir nesneyi, diğer VSTO çözümler de dahil olmak üzere diğer çözümlere eklenti olarak Microsoft Office sebilirsiniz. Bu, VSTO eklentinizin diğer çözümlerin kullanmalarını sağlamak istediğiniz bir hizmet sağladığında kullanışlıdır. Örneğin, web VSTO web Microsoft Office Excel üzerinde hesaplamalar yapan bir VSTO Eklentiniz varsa, diğer çözümler çalışma zamanında Excel VSTO Eklentisini çağırarak bu hesaplamaları gerçekleştirebilirsiniz.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

 Bu süreçte iki ana adım vardır:

- Uygulama VSTO, bir nesneyi diğer çözümlere açık şekilde gösterir.

- Başka bir çözümde, eklentiniz tarafından VSTO nesnesine erişin ve nesnenin üyelerini çağırın.

## <a name="types-of-solutions-that-can-call-code-in-an-add-in"></a>Eklentide kod çağıran çözüm türleri
 Bir nesneyi aşağıdaki çözüm VSTO eklentisinde ortaya çıkarabilirsiniz:

- Visual Basic for Applications eklentiniz ile aynı uygulama sürecinde yüklenen bir belgeye (VBA) VSTO ekleyin.

- Uygulama eklentiniz ile aynı uygulama sürecinde yüklenen belge düzeyinde VSTO özelleştirmeler.

- Diğer VSTO proje şablonları kullanılarak oluşturulan diğer Office şablonları Visual Studio.

- COM VSTO eklentileri (diğer bir VSTO arabirimi uygulayan <xref:Extensibility.IDTExtensibility2> eklentiler) içerir.

- Eklentiden farklı bir işlemde çalışan VSTO çözümler (bu tür çözümlere işlem dışında *istemciler de denir).* Bunlar, Windows Forms veya konsol uygulaması gibi bir Office uygulamasını otomatikleştiren uygulamaları ve VSTO bir işlemde yüklenen eklentilerini içerir.

## <a name="expose-objects-to-other-solutions"></a>Nesneleri diğer çözümlere maruz
 Bir nesneyi diğer çözümlere VSTO eklentisinde göstermek için, eklentinizin eklentisinde VSTO gerçekleştirin:

1. Diğer çözümlerin ortaya çıkarmak istediğiniz bir sınıf tanımlayın.

2. sınıfındaki <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> yöntemini geçersiz `ThisAddIn` kılın. Diğer çözümlerin ortaya çıkarmak istediğiniz sınıfının bir örneğini dönüş.

### <a name="define-the-class-you-want-to-expose-to-other-solutions"></a>Diğer çözümlerin ortaya çıkarmak istediğiniz sınıfını tanımlayın
 En azından, ortaya çıkarmak istediğiniz sınıf genel olmalı, özniteliği true olarak ayar olmalı ve <xref:System.Runtime.InteropServices.ComVisibleAttribute> [IDispatch arabirimini açığa çıkarmalı.](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) 

 [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) arabirimini ortaya çıkarmanın önerilen yolu aşağıdaki adımları gerçekleştirmektir:

1. Diğer çözümlere göstermek istediğiniz üyeleri bildiren bir arabirim tanımlayın. Bu arabirimi eklenti projesinde VSTO tanımlayabilirsiniz. Ancak, sınıfını VBA olmayan çözümlerin kullanımına göstermek, böylece VSTO Eklentinizi çağıran çözümlerin VSTO Eklenti projenize başvurmadan arabirime başvuramalarını sağlarsanız, bu arabirimi ayrı bir sınıf kitaplığı projesinde tanımlamak iyi olabilir.

2. özniteliğini <xref:System.Runtime.InteropServices.ComVisibleAttribute> bu arabirime uygulayan ve bu özniteliği true olarak **ayarlayın.**

3. Bu arabirimi uygulamak için sınıfınızı değiştirme.

4. özniteliğini <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> sınıfınıza uygulama ve bu özniteliği numaralamanın **None** <xref:System.Runtime.InteropServices.ClassInterfaceType> değerine ayarlayın.

5. Bu sınıfı işlem dışında istemcilere göstermek için aşağıdaki işlemleri de gerçekleştirin:

   - sınıfından sınıfını <xref:System.Runtime.InteropServices.StandardOleMarshalObject> türetin. Daha fazla bilgi için [bkz. Sınıfları işlem dışında istemcilerde ortaya çıkarma.](#outofproc)

   - Arabirimi **tanımladığınız projede COM birlikte** çalışma özelliğine kaydol özelliğini ayarlayın. Bu özellik yalnızca istemcilerin eklentiye çağrı yapmak için erken bağlama kullanmalarını sağlamak VSTO gereklidir.

   Aşağıdaki kod örneği, diğer çözümler `AddInUtilities` tarafından `ImportData` çağrılabilir yöntemine sahip bir sınıfını gösteriyor. Bu kodu daha büyük bir izlenecek yol bağlamında görmek için bkz. [Kılavuz: VBA'dan VSTO eklentisinde kod çağırma.](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)

   :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/AddInUtilities.cs" id="Snippet3":::
   :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/AddInUtilities.vb" id="Snippet3":::

### <a name="expose-classes-to-vba"></a>Sınıfları VBA'ya maruz
 Yukarıda sağlanan adımları gerçekleştirin, VBA kodu yalnızca arabirimde bildirdiğimiz yöntemleri çağırabilir. VBA kodu, sınıfınız gibi temel sınıflardan edinilen yöntemler de dahil olmak üzere sınıfınıza başka yöntemler <xref:System.Object> çağıramaz.

 [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) arabirimini alternatif olarak, özniteliğini numaralamanın AutoDispatch veya AutoDual değerine ayarlayarak <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> da ortaya <xref:System.Runtime.InteropServices.ClassInterfaceType> çıkarabilirsiniz. Arabirimini açığa çıkarırsanız, yöntemleri ayrı bir arabirimde bildirebilirsiniz. Ancak VBA kodu, gibi temel sınıflardan alınan yöntemler de dahil olmak üzere sınıfınıza herhangi bir genel ve statik olmayan yöntemi <xref:System.Object> çağırabilir. Ayrıca, erken bağlama kullanan işlem dışında istemciler sınıfınızı çağıramaz.

### <a name="expose-classes-to-out-of-process-clients"></a><a name="outofproc"></a> Sınıfları işlem dışında istemcilerde ortaya çıkarma
 VSTO Eklentisinde bir sınıfı işlem olmayan istemcilere göstermek için, işlem dışında istemcilerin açığa çıkarnan VSTO Add-in nesnenizi çağıramalarını sağlamak için sınıfından <xref:System.Runtime.InteropServices.StandardOleMarshalObject> türetebilirsiniz. Aksi takdirde, işlem dışında bir istemcide açığa çıkar durumdaki nesnenizin bir örneğini almaya yönelik girişimler beklenmedik şekilde başarısız olabilir.

 Bunun nedeni, bir Office uygulamasının nesne modeline yapılan tüm çağrıların ana kullanıcı arabirimi iş parçacığında yapılmış olması, ancak işlem dışı istemciden nesnenize yapılan çağrılar rastgele rpc (uzak yordam çağrısı) iş parçacığına ulaşacak olmasıdır. .NET Framework'daki COM sıralama mekanizması, iş parçacıklarını değiştirmez ve bunun yerine çağrıyı ana kullanıcı arabirimi iş parçacığı yerine gelen RPC iş parçacığında nesnenize sıralamaya çalışır. Nesneniz, sınıfından türetilen bir sınıfın örneği ise, nesnenize gelen çağrılar, ana uygulamanın ana kullanıcı arabirimi iş parçacığı olacak şekilde, açığa çıkarılan nesnenin oluşturulacak iş parçacığına otomatik olarak <xref:System.Runtime.InteropServices.StandardOleMarshalObject> sıralanmış olur.

 İş parçacıklarını farklı çözümlerde kullanma hakkında daha Office için [bkz.](../vsto/threading-support-in-office.md)Office.

### <a name="override-the-requestcomaddinautomationservice-method"></a>RequestComAddInAutomationService yöntemini geçersiz kılma
 Aşağıdaki kod örneği, eklentinizin <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> sınıfını `ThisAddIn` geçersiz kılmayı VSTO gösteriyor. Örnekte, diğer çözümlerin ortaya çıkarmak istediğiniz adlı `AddInUtilities` bir sınıf tanımlandığı varsaymaktadır. Bu kodu daha büyük bir izlenecek yol bağlamında görmek için bkz. [Kılavuz: VBA'dan VSTO eklentisinde kod çağırma.](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/ThisAddIn.cs" id="Snippet1":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/ThisAddIn.vb" id="Snippet1":::

 VSTO eklentiniz yüklendiğinde [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] yöntemini <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> çağıran. Çalışma zamanı, döndürülen nesneyi eklentinizi temsil eden bir nesnenin COMAddIn.Object <xref:Microsoft.Office.Core.COMAddIn> özelliğine VSTO atar. Bu <xref:Microsoft.Office.Core.COMAddIn> nesne, diğer Office çözümleri ve bu çözümleri otomatikleştiren Office.

## <a name="access-objects-from-other-solutions"></a>Diğer çözümlerden nesnelere erişme
 Eklentinizin içinde açığa VSTO için istemci çözümünde aşağıdaki adımları gerçekleştirin:

1. Açık <xref:Microsoft.Office.Core.COMAddIn> olan eklentiyi temsil eden VSTO elde edersiniz. İstemciler, konak VSTO nesne modelinde özelliğini kullanarak tüm kullanılabilir Office `Application.COMAddIns` erişebilir.

2. Nesnenin COMAddIn.Object özelliğine <xref:Microsoft.Office.Core.COMAddIn> erişin. Bu özellik, eklentinin VSTO nesnesini döndürür.

3. Ortaya çıkaran nesnenin üyelerini çağırma.

   COMAddIn.Object özelliğinin dönüş değerini kullanma şekliniz VBA istemcileri ve VBA olmayan istemciler için farklıdır. İşlem dışında olan istemciler için olası bir yarış durumundan kaçınmak için ek kod gerekir.

### <a name="access-objects-from-vba-solutions"></a>VBA çözümlerinden nesnelere erişme
 Aşağıdaki kod örneği, bir uygulama eklentisinde bir eklenti tarafından ortaya çıkar bir yöntem çağrısı yapmak için VBA'VSTO nasıl gösterileceğini gösteriyor. Bu VBA `ImportData` **makrosu, ExcelImportData** adlı bir VSTO içinde tanımlanan adlı bir yöntemi çağırıyor. Bu kodu daha büyük bir izlenecek yol bağlamında görmek için bkz. [Kılavuz: VBA'dan VSTO eklentisinde kod çağırma.](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)

```vb
Sub CallVSTOMethod()
    Dim addIn As COMAddIn
    Dim automationObject As Object
    Set addIn = Application.COMAddIns("ExcelImportData")
    Set automationObject = addIn.Object
    automationObject.ImportData
End Sub
```

### <a name="access-objects-from-non-vba-solutions"></a>VBA olmayan çözümlerden nesnelere erişme
 VBA olmayan bir çözümde COMAddIn.Object özellik değerini uygulayan arabirime atarak arabirim nesnesinde ortaya konu olan yöntemleri çağırabilirsiniz. Aşağıdaki kod örneği, Office geliştirici araçları kullanılarak oluşturulan farklı bir VSTO Eklentiden yönteminin nasıl `ImportData` çağrıl Visual Studio.

```vb
Dim addIn As Office.COMAddIn = Globals.ThisAddIn.Application.COMAddIns.Item("ExcelImportData")
Dim utilities As ExcelImportData.IAddInUtilities = TryCast( _
    addIn.Object, ExcelImportData.IAddInUtilities)
utilities.ImportData()
```

```csharp
object addInName = "ExcelImportData";
Office.COMAddIn addIn = Globals.ThisAddIn.Application.COMAddIns.Item(ref addInName);
ExcelImportData.IAddInUtilities utilities = (ExcelImportData.IAddInUtilities)addIn.Object;
utilities.ImportData();
```

 Bu örnekte COMAddIn.Object özelliğinin değerini arabirim yerine sınıfına atmayı denersanız `AddInUtilities` `IAddInUtilities` kod bir <xref:System.InvalidCastException> oluşturur.

## <a name="see-also"></a>Ayrıca bkz.
- [Program VSTO Eklentileri](../vsto/programming-vsto-add-ins.md)
- [Kılavuz: VBA'dan VSTO eklentisinde kod çağırma](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)
- [Yeni Office geliştirme](../vsto/developing-office-solutions.md)
- [Nasıl Office: Visual Studio'da Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [VSTO Eklentileri Mimarisi](../vsto/architecture-of-vsto-add-ins.md)
- [Genişletilebilirlik arabirimlerini kullanarak kullanıcı arabirimi özelliklerini özelleştirme](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)
