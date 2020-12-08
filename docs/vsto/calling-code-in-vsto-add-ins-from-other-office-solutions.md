---
title: Diğer Office çözümlerindeki VSTO eklentilerindeki kodu çağırma
description: VSTO eklentiinizdeki bir nesneyi diğer Microsoft Office çözümleri de dahil olmak üzere diğer çözümlere nasıl kullanıma sunabileceğiniz hakkında bilgi edinin.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fad3f107487e4736ccd0a6aa59ea5a801b5f72e5
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96847851"
---
# <a name="call-code-in-vsto-add-ins-from-other-office-solutions"></a>Diğer Office çözümlerindeki VSTO eklentilerindeki kodu çağırma
  VSTO eklentiinizdeki bir nesneyi diğer Microsoft Office çözümleri de dahil olmak üzere diğer çözümlere kullanıma sunabilirsiniz. Bu, VSTO eklentisinin diğer çözümlerin kullanmasını sağlamak istediğiniz bir hizmet sağlıyorsa yararlı olur. Örneğin, bir Web hizmetinden finans verilerinde hesaplamalar gerçekleştiren Microsoft Office Excel için bir VSTO eklentileriniz varsa, diğer çözümler çalışma zamanında Excel VSTO eklentisini çağırarak bu hesaplamaları gerçekleştirebilir.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

 Bu işlemde iki ana adım vardır:

- VSTO eklentilerinizde, bir nesneyi diğer çözümlere sunun.

- Başka bir çözümde, VSTO eklentisi tarafından kullanıma sunulan nesneye erişin ve nesnesinin üyelerini çağırın.

## <a name="types-of-solutions-that-can-call-code-in-an-add-in"></a>Bir eklentideki kodu çağırabilirler çözüm türleri
 Bir VSTO eklentisinin içindeki bir nesneyi aşağıdaki türlerde çözümler halinde kullanıma sunabilirsiniz:

- VSTO eklentiinizdeki aynı uygulama işleminde yüklü olan bir belgedeki Visual Basic for Applications (VBA) kodu.

- VSTO eklentilerinizle aynı uygulama sürecinde yüklenen belge düzeyi özelleştirmeleri.

- Visual Studio 'da Office proje şablonları kullanılarak oluşturulan diğer VSTO eklentileri.

- COM VSTO eklentileri (diğer bir deyişle, arabirimi doğrudan uygulayan VSTO eklentileri <xref:Extensibility.IDTExtensibility2> ).

- VSTO eklentiinizdeki farklı bir işlemde çalışan herhangi bir çözüm (Bu tür çözümler, *işlem dışı istemciler* olarak da adlandırılır). Bunlar, bir Office uygulamasını otomatikleştiren bir Windows Forms veya konsol uygulaması ve farklı bir işlemde yüklenen VSTO eklentileri gibi uygulamaları içerir.

## <a name="expose-objects-to-other-solutions"></a>Nesneleri diğer çözümlere sunma
 VSTO eklentiinizdeki bir nesneyi diğer çözümlere sunmak için, VSTO eklentilerinizde aşağıdaki adımları gerçekleştirin:

1. Diğer çözümlere sunmak istediğiniz bir sınıf tanımlayın.

2. <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A>Sınıfında yöntemi geçersiz kılın `ThisAddIn` . Diğer çözümlere sunmak istediğiniz sınıfın bir örneğini döndürün.

### <a name="define-the-class-you-want-to-expose-to-other-solutions"></a>Diğer çözümlere sunmak istediğiniz sınıfı tanımlayın
 En azından, göstermek istediğiniz sınıfın public olması gerekir, <xref:System.Runtime.InteropServices.ComVisibleAttribute> özniteliği **true** olarak ayarlanmalıdır ve [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) arabirimini kullanıma sunmalıdır.

 [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) arabirimini kullanıma sunmak için önerilen yol aşağıdaki adımları gerçekleştirmedir:

1. Diğer çözümlere sunmak istediğiniz üyeleri bildiren bir arabirim tanımlayın. Bu arabirimi, VSTO eklenti projenizde tanımlayabilirsiniz. Ancak, sınıfı VBA olmayan çözümlere göstermek istiyorsanız bu arabirimi ayrı bir sınıf kitaplığı projesinde tanımlamak isteyebilirsiniz. bu sayede, VSTO eklentisini çağıran çözümlerin, VSTO eklenti projenize başvurulmadan arabirime başvurabilmesi gerekir.

2. <xref:System.Runtime.InteropServices.ComVisibleAttribute>Özniteliği bu arabirime uygulayın ve bu özniteliği **true** olarak ayarlayın.

3. Bu arabirimi uygulamak için sınıfınızı değiştirin.

4. <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>Özniteliğini sınıfınıza uygulayın ve bu özniteliği numaralandırmanın **none** değerine ayarlayın <xref:System.Runtime.InteropServices.ClassInterfaceType> .

5. Bu sınıfı işlem dışı istemcilere göstermek istiyorsanız aşağıdakileri de yapmanız gerekebilir:

   - Sınıfından türet <xref:System.Runtime.InteropServices.StandardOleMarshalObject> . Daha fazla bilgi için bkz. [sınıfları işlem dışı istemcilere](#outofproc)sunma.

   - Arabirimini tanımladığınız projede **com birlikte çalışma özelliğini kaydet** özelliğini ayarlayın. Bu özellik yalnızca, istemcilerin VSTO eklentisini çağırmak için erken bağlamayı kullanmasını etkinleştirmek istiyorsanız gereklidir.

   Aşağıdaki kod örneği, `AddInUtilities` `ImportData` diğer çözümler tarafından çağrılabilecek bir yöntemi olan bir sınıfı gösterir. Daha büyük bir anlatım bağlamında bu kodu görmek için bkz. [Izlenecek yol: BIR VSTO EKLENTISINDE VBA 'Dan çağrı kodu](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).

   [!code-csharp[Trin_AddInInteropWalkthrough #3](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/AddInUtilities.cs#3)]
   [!code-vb[Trin_AddInInteropWalkthrough#3](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/AddInUtilities.vb#3)]

### <a name="expose-classes-to-vba"></a>Sınıfları VBA 'da kullanıma sunma
 Yukarıda belirtilen adımları gerçekleştirdiğinizde, VBA kodu yalnızca arabirimde bildirdiğiniz yöntemleri çağırabilir. VBA kodu, sınıfınızın gibi temel sınıflardan elde ettiği yöntemler de dahil olmak üzere sınıfınıza başka yöntemler çağrılamaz <xref:System.Object> .

 Alternatif olarak, sıralamasının [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> oto ya da oto Dual değerine ayarlayarak IDispatch arabirimini kullanıma sunabilirsiniz <xref:System.Runtime.InteropServices.ClassInterfaceType> . Arabirimi kullanıma sunmanız durumunda, yöntemleri ayrı bir arabirimde bildirmeniz gerekmez. Ancak, VBA kodu, gibi temel sınıflardan edinilen yöntemler de dahil olmak üzere sınıfınızdan ortak ve statik olmayan yöntemleri çağırabilir <xref:System.Object> . Ayrıca, erken bağlama kullanan işlem dışı istemciler sınıfınızı çağıramaz.

### <a name="expose-classes-to-out-of-process-clients"></a><a name="outofproc"></a> Sınıfları işlem dışı istemcilerde kullanıma sunma
 VSTO eklentiinizdeki bir sınıfı işlem dışı istemcilere sunmak istiyorsanız, <xref:System.Runtime.InteropServices.StandardOleMarshalObject> işlem dışı istemcilerin sunulan VSTO eklenti nesnesini çağırabilecekleri şekilde sınıfından sınıfını türetirsiniz... Aksi takdirde, işlem dışı bir istemcide kullanıma sunulan nesnenizin bir örneğini alma girişimleri beklenmedik şekilde başarısız olabilir.

 Bu hata, bir Office uygulamasının nesne modeline yapılan tüm çağrıların ana kullanıcı arabirimi iş parçacığında yapılması gerekir, ancak işlem dışı bir istemciden nesnenizin çağrısı, rastgele bir RPC (uzak yordam çağrısı) iş parçacığına ulaşır. .NET Framework COM sıralama mekanizması iş parçacıklarını değiştirmez ve bunun yerine, ana UI iş parçacığı yerine gelen RPC iş parçacığında nesneniz için çağrıyı sıralaması gerekir. Nesneniz öğesinden türetilen bir sınıfın bir örneği ise <xref:System.Runtime.InteropServices.StandardOleMarshalObject> , nesneniz için gelen çağrılar, ana bilgisayar uygulamasının ana kullanıcı arabirimi iş parçacığı olacak şekilde, gösterilen nesnenin oluşturulduğu iş parçacığına otomatik olarak sıralanır.

 Office çözümlerinde iş parçacıklarını kullanma hakkında daha fazla bilgi için bkz. [Office 'Te Iş parçacığı desteği](../vsto/threading-support-in-office.md).

### <a name="override-the-requestcomaddinautomationservice-method"></a>RequestComAddInAutomationService yöntemini geçersiz kılma
 Aşağıdaki kod örneği, <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> VSTO eklentiinizdeki sınıfında nasıl geçersiz kılınacağını göstermektedir `ThisAddIn` . Örnek, diğer çözümlere sunmak istediğiniz adlı bir sınıf tanımlamış olduğunuzu varsayar `AddInUtilities` . Daha büyük bir anlatım bağlamında bu kodu görmek için bkz. [Izlenecek yol: BIR VSTO EKLENTISINDE VBA 'Dan çağrı kodu](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).

 [!code-csharp[Trin_AddInInteropWalkthrough#1](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/ThisAddIn.cs#1)]
 [!code-vb[Trin_AddInInteropWalkthrough#1](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/ThisAddIn.vb#1)]

 VSTO eklentisi yüklendiğinde, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> yöntemini çağırır. Çalışma zamanı, döndürülen nesneyi <xref:Microsoft.Office.Core.COMAddIn> VSTO eklentisini temsil eden bir nesnenin COMAddIn. Object özelliğine atar. Bu <xref:Microsoft.Office.Core.COMAddIn> nesne diğer Office çözümleri ve Office 'i otomatikleştiren çözümler için kullanılabilir.

## <a name="access-objects-from-other-solutions"></a>Diğer çözümlerdeki nesnelere erişme
 VSTO eklentiinizdeki sunulan nesneyi çağırmak için, istemci çözümünde aşağıdaki adımları gerçekleştirin:

1. <xref:Microsoft.Office.Core.COMAddIn>Sunulan VSTO eklentisini temsil eden nesneyi alır. İstemciler, `Application.COMAddIns` ana bilgisayar Office uygulamasının nesne modelindeki özelliğini kullanarak tüm KULLANILABILIR VSTO eklentilerine erişebilir.

2. Nesnenin COMAddIn. Object özelliğine erişin <xref:Microsoft.Office.Core.COMAddIn> . Bu özellik, VSTO eklentiden sunulan nesneyi döndürür.

3. Gösterilen nesnenin üyelerini çağırın.

   COMAddIn. Object özelliğinin dönüş değerini kullanma yöntemi, VBA istemcileri ve VBA olmayan istemciler için farklıdır. İşlem dışı istemcilerde, olası bir yarış durumundan kaçınmak için ek kod gereklidir.

### <a name="access-objects-from-vba-solutions"></a>VBA çözümlerinde nesnelere erişme
 Aşağıdaki kod örneği, bir VSTO eklentisi tarafından sunulan bir yöntemi çağırmak için VBA 'Yı nasıl kullanacağınızı gösterir. Bu VBA makrosu `ImportData` , **ExcelImportData** adlı bir VSTO eklentisinde tanımlanmış adlı bir yöntemi çağırır. Daha büyük bir anlatım bağlamında bu kodu görmek için bkz. [Izlenecek yol: BIR VSTO EKLENTISINDE VBA 'Dan çağrı kodu](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).

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
 VBA olmayan bir çözümde, COMAddIn. Object Özellik değerini uyguladığı arabirime atamalısınız ve sonra arabirim nesnesi üzerinde sunulan yöntemleri çağırabilirsiniz. Aşağıdaki kod örneği, `ImportData` Visual Studio 'Da Office geliştirici araçları kullanılarak oluşturulmuş farklı bır VSTO eklentisinin yönteminin nasıl çağrılacağını gösterir.

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

 Bu örnekte, COMAddIn. Object özelliğinin değerini `AddInUtilities` arabirimi yerine sınıfına dönüştürmeye çalışırsanız `IAddInUtilities` , kod bir oluşturur <xref:System.InvalidCastException> .

## <a name="see-also"></a>Ayrıca bkz.
- [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md)
- [İzlenecek yol: bir VSTO eklentisinde VBA 'dan kod çağırma](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)
- [Office çözümleri geliştirme](../vsto/developing-office-solutions.md)
- [Nasıl yapılır: Visual Studio 'da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [VSTO Eklentileri Mimarisi](../vsto/architecture-of-vsto-add-ins.md)
- [Genişletilebilirlik arabirimlerini kullanarak Kullanıcı arabirimi özelliklerini özelleştirme](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)
