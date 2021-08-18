---
title: diğer Office çözümlerdeki VSTO eklentilerdeki kodu çağırma
description: diğer Microsoft Office çözümleri de dahil olmak üzere VSTO eklentiinizdeki bir nesneyi diğer çözümlere nasıl sergilebileceğinizi öğrenin.
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
ms.openlocfilehash: 857cff3d396cfa08d45d7c15bc9b045f7fe23f0c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122083706"
---
# <a name="call-code-in-vsto-add-ins-from-other-office-solutions"></a>diğer Office çözümlerdeki VSTO eklentilerdeki kodu çağırma
  VSTO eklentiinizdeki bir nesneyi diğer Microsoft Office çözümleri de dahil olmak üzere diğer çözümlere kullanıma sunabilirsiniz. VSTO eklentisi, diğer çözümlerin kullanımını etkinleştirmek istediğiniz bir hizmet sağlıyorsa bu kullanışlıdır. örneğin, bir Web hizmetinden finansal veriler üzerinde hesaplamalar gerçekleştiren Microsoft Office Excel için VSTO bir eklentiye sahipseniz, diğer çözümler çalışma zamanında Excel VSTO eklentiye çağırarak bu hesaplamaları gerçekleştirebilir.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

 Bu işlemde iki ana adım vardır:

- VSTO eklentilerinizde, bir nesneyi diğer çözümlere sunun.

- başka bir çözümde, VSTO eklentisi tarafından kullanıma sunulan nesneye erişin ve nesnesinin üyelerini çağırın.

## <a name="types-of-solutions-that-can-call-code-in-an-add-in"></a>Bir eklentideki kodu çağırabilirler çözüm türleri
 bir VSTO eklentisi içindeki bir nesneyi aşağıdaki çözüm türlerine ulaşılabilir yapabilirsiniz:

- VSTO eklentiinizdeki aynı uygulama işleminde yüklü olan bir belgedeki Visual Basic for Applications (VBA) kodu.

- VSTO eklentisi ile aynı uygulama işlemine yüklenen belge düzeyi özelleştirmeleri.

- Visual Studio içindeki Office proje şablonları kullanılarak oluşturulan diğer VSTO eklentileri.

- COM VSTO eklentiler (diğer bir deyişle, arabirimi doğrudan uygulayan eklentiler VSTO <xref:Extensibility.IDTExtensibility2> ).

- VSTO eklentilerinizle farklı bir işlemde çalışan herhangi bir çözüm (bu tür çözümler *işlem dışı istemciler* olarak da adlandırılır). bunlar, bir Windows Forms ya da konsol uygulaması gibi Office uygulamasını otomatikleştiren uygulamalar ve farklı bir işlemde yüklenen VSTO eklentileri içerir.

## <a name="expose-objects-to-other-solutions"></a>Nesneleri diğer çözümlere sunma
 VSTO eklentiinizdeki bir nesneyi diğer çözümlere sunmak için, VSTO eklentilerinizde aşağıdaki adımları gerçekleştirin:

1. Diğer çözümlere sunmak istediğiniz bir sınıf tanımlayın.

2. <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A>Sınıfında yöntemi geçersiz kılın `ThisAddIn` . Diğer çözümlere sunmak istediğiniz sınıfın bir örneğini döndürün.

### <a name="define-the-class-you-want-to-expose-to-other-solutions"></a>Diğer çözümlere sunmak istediğiniz sınıfı tanımlayın
 En azından, göstermek istediğiniz sınıfın public olması gerekir, <xref:System.Runtime.InteropServices.ComVisibleAttribute> özniteliği **true** olarak ayarlanmalıdır ve [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) arabirimini kullanıma sunmalıdır.

 [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) arabirimini kullanıma sunmak için önerilen yol aşağıdaki adımları gerçekleştirmedir:

1. Diğer çözümlere sunmak istediğiniz üyeleri bildiren bir arabirim tanımlayın. bu arabirimi, VSTO eklenti projenizde tanımlayabilirsiniz. ancak, sınıfı VBA olmayan çözümlere göstermek istiyorsanız, bu arabirimi ayrı bir sınıf kitaplığı projesinde tanımlamak isteyebilirsiniz. böylece, VSTO eklentisini çağıran çözümlerin, VSTO eklenti projenize başvurulmadan arabirime başvurabilmesi gerekir.

2. <xref:System.Runtime.InteropServices.ComVisibleAttribute>Özniteliği bu arabirime uygulayın ve bu özniteliği **true** olarak ayarlayın.

3. Bu arabirimi uygulamak için sınıfınızı değiştirin.

4. <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>Özniteliğini sınıfınıza uygulayın ve bu özniteliği numaralandırmanın **none** değerine ayarlayın <xref:System.Runtime.InteropServices.ClassInterfaceType> .

5. Bu sınıfı işlem dışı istemcilere göstermek istiyorsanız aşağıdakileri de yapmanız gerekebilir:

   - Sınıfından türet <xref:System.Runtime.InteropServices.StandardOleMarshalObject> . Daha fazla bilgi için bkz. [sınıfları işlem dışı istemcilere](#outofproc)sunma.

   - Arabirimini tanımladığınız projede **com birlikte çalışma özelliğini kaydet** özelliğini ayarlayın. bu özellik yalnızca, istemcilerin VSTO eklentiye çağırmak için erken bağlamayı kullanmasını etkinleştirmek istiyorsanız gereklidir.

   Aşağıdaki kod örneği, `AddInUtilities` `ImportData` diğer çözümler tarafından çağrılabilecek bir yöntemi olan bir sınıfı gösterir. daha büyük bir anlatım bağlamında bu kodu görmek için bkz. [izlenecek yol: VSTO eklentisinde VBA 'dan çağrı kodu](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).

   :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/AddInUtilities.cs" id="Snippet3":::
   :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/AddInUtilities.vb" id="Snippet3":::

### <a name="expose-classes-to-vba"></a>Sınıfları VBA 'da kullanıma sunma
 Yukarıda belirtilen adımları gerçekleştirdiğinizde, VBA kodu yalnızca arabirimde bildirdiğiniz yöntemleri çağırabilir. VBA kodu, sınıfınızın gibi temel sınıflardan elde ettiği yöntemler de dahil olmak üzere sınıfınıza başka yöntemler çağrılamaz <xref:System.Object> .

 Alternatif olarak, sıralamasının [](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> oto ya da oto Dual değerine ayarlayarak IDispatch arabirimini kullanıma sunabilirsiniz <xref:System.Runtime.InteropServices.ClassInterfaceType> . Arabirimi kullanıma sunmanız durumunda, yöntemleri ayrı bir arabirimde bildirmeniz gerekmez. Ancak, VBA kodu, gibi temel sınıflardan edinilen yöntemler de dahil olmak üzere sınıfınızdan ortak ve statik olmayan yöntemleri çağırabilir <xref:System.Object> . Ayrıca, erken bağlama kullanan işlem dışı istemciler sınıfınızı çağıramaz.

### <a name="expose-classes-to-out-of-process-clients"></a><a name="outofproc"></a> Sınıfları işlem dışı istemcilerde kullanıma sunma
 VSTO eklentiinizdeki bir sınıfı işlem dışı istemcilere sunmak istiyorsanız, <xref:System.Runtime.InteropServices.StandardOleMarshalObject> işlem dışı istemcilerin sunulan VSTO eklenti nesnesini çağırabilecekleri emin olmak için sınıfından sınıfını türetebilirsiniz. Aksi takdirde, işlem dışı bir istemcide kullanıma sunulan nesnenizin bir örneğini alma girişimleri beklenmedik şekilde başarısız olabilir.

 bu hata, ana kullanıcı arabirimi iş parçacığında bir Office uygulamanın nesne modeline yapılan çağrıların yapılması ve bir işlem dışı istemciden nesneniz arasında yapılan çağrıların rastgele bir RPC (uzak yordam çağrısı) iş parçacığına ulaşacak olması nedeniyle oluşur. .NET Framework COM sıralama mekanizması iş parçacıklarını değiştirmez ve bunun yerine, ana uı iş parçacığı yerine gelen RPC iş parçacığında nesneniz için çağrıyı sıralaması gerekir. Nesneniz öğesinden türetilen bir sınıfın bir örneği ise <xref:System.Runtime.InteropServices.StandardOleMarshalObject> , nesneniz için gelen çağrılar, ana bilgisayar uygulamasının ana kullanıcı arabirimi iş parçacığı olacak şekilde, gösterilen nesnenin oluşturulduğu iş parçacığına otomatik olarak sıralanır.

 Office çözümlerinde iş parçacıklarını kullanma hakkında daha fazla bilgi için bkz. [Office 'da iş parçacığı oluşturma desteği](../vsto/threading-support-in-office.md).

### <a name="override-the-requestcomaddinautomationservice-method"></a>RequestComAddInAutomationService yöntemini geçersiz kılma
 aşağıdaki kod örneği, <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> VSTO eklentiinizdeki sınıfında nasıl geçersiz kılınacağını göstermektedir `ThisAddIn` . Örnek, diğer çözümlere sunmak istediğiniz adlı bir sınıf tanımlamış olduğunuzu varsayar `AddInUtilities` . daha büyük bir anlatım bağlamında bu kodu görmek için bkz. [izlenecek yol: VSTO eklentisinde VBA 'dan çağrı kodu](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/ThisAddIn.cs" id="Snippet1":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/ThisAddIn.vb" id="Snippet1":::

 VSTO eklentisi yüklendiğinde, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> yöntemini çağırır. çalışma zamanı, döndürülen nesneyi <xref:Microsoft.Office.Core.COMAddIn> VSTO eklentisini temsil eden bir nesnenin COMAddIn. object özelliğine atar. bu <xref:Microsoft.Office.Core.COMAddIn> nesne diğer Office çözümleri ve Office otomatikleştiren çözümler için kullanılabilir.

## <a name="access-objects-from-other-solutions"></a>Diğer çözümlerdeki nesnelere erişme
 VSTO eklentiinizdeki sunulan nesneyi çağırmak için, istemci çözümünde aşağıdaki adımları gerçekleştirin:

1. <xref:Microsoft.Office.Core.COMAddIn>sunulma VSTO eklentisini temsil eden nesneyi alır. istemciler, `Application.COMAddIns` ana bilgisayar Office uygulamasının nesne modelindeki özelliğini kullanarak kullanılabilir VSTO eklentilerine erişebilir.

2. Nesnenin COMAddIn. Object özelliğine erişin <xref:Microsoft.Office.Core.COMAddIn> . bu özellik VSTO eklentiden sunulan nesneyi döndürür.

3. Gösterilen nesnenin üyelerini çağırın.

   COMAddIn. Object özelliğinin dönüş değerini kullanma yöntemi, VBA istemcileri ve VBA olmayan istemciler için farklıdır. İşlem dışı istemcilerde, olası bir yarış durumundan kaçınmak için ek kod gereklidir.

### <a name="access-objects-from-vba-solutions"></a>VBA çözümlerinde nesnelere erişme
 aşağıdaki kod örneği, bir VSTO eklentisi tarafından sunulan bir yöntemi çağırmak için VBA 'yı nasıl kullanacağınızı gösterir. bu VBA makrosu `ImportData` , **excelımportdata** adlı bir VSTO eklentisinde tanımlanmış adlı bir yöntemi çağırır. daha büyük bir anlatım bağlamında bu kodu görmek için bkz. [izlenecek yol: VSTO eklentisinde VBA 'dan çağrı kodu](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).

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
 VBA olmayan bir çözümde, COMAddIn. Object Özellik değerini uyguladığı arabirime atamalısınız ve sonra arabirim nesnesi üzerinde sunulan yöntemleri çağırabilirsiniz. aşağıdaki kod örneği, `ImportData` Visual Studio ' de Office geliştirici araçları kullanılarak oluşturulan farklı bir VSTO eklentisinin yönteminin nasıl çağrılacağını gösterir.

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
- [izlenecek yol: VSTO eklentisinde VBA 'dan kod çağırma](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)
- [Office çözümleri geliştirme](../vsto/developing-office-solutions.md)
- [nasıl yapılır: Visual Studio Office projeler oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [VSTO Eklentileri Mimarisi](../vsto/architecture-of-vsto-add-ins.md)
- [Genişletilebilirlik arabirimlerini kullanarak Kullanıcı arabirimi özelliklerini özelleştirme](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)
