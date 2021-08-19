---
title: VBA ve belge düzeyi özelleştirmelerini birleştirme
description: Word veya Visual Basic for Applications için belge düzeyi özelleştirmenin bir parçası olan belge içinde Microsoft Office (VBA) Excel.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.VBAInterop.InvalidAssemblyVersion
- VST.VBAInterop.ProjectLoadFailure
- VST.VBAInterop.MissingGUID
- VST.VBAInterop.EnableComCallers
- VST.VBAInterop.PersistVBACode
- VST.VBAInterop.ReferenceAssemblyFromVBA
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], Visual Basic for Applications and
- VBA [Office development in Visual Studio]
- Office documents [Office development in Visual Studio], Visual Basic for Applications and
- VBA [Office development in Visual Studio], about VBA and document-level customizations
- managed code [Office development in Visual Studio], Visual Basic for Applications and
- document-level customizations [Office development in Visual Studio], Visual Basic for Applications and
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: c29399119ffaff26be670a6fee88d8de3c92368c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122053956"
---
# <a name="combine-vba-and-document-level-customizations"></a>VBA ve belge düzeyi özelleştirmelerini birleştirme
  Word veya Visual Basic for Applications için belge düzeyi özelleştirmenin bir parçası olan bir belgede Microsoft Office (VBA) Microsoft Office Excel. Belgede VBA kodunu özelleştirme derlemesinde çağırabilir veya projenizi, belgede VBA kodunu özelleştirme derlemesinde kod çağırarak etkinleştirecek şekilde yapılandırabilirsiniz.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="behavior-of-vba-code-in-a-document-level-customization"></a>Belge düzeyinde özelleştirmede VBA kodunun davranışı
 Projenizi yeni bir Visual Studio, belge tasarım modunda açılır. Belge tasarım modundayken VBA kodu çalışmaz, bu nedenle VBA kodunu çalıştırmadan belge ve kod üzerinde çalışabilirsiniz.

 Çözümü çalıştırarak hem VBA hem de özelleştirme derlemesinde olay işleyicileri belgede ortaya çıkar ve her iki kod kümesi de çalıştırıldı. Hangi kodun diğer kodun önünde çalıştırılamayacaklarını önceden belirleyesiniz; Bunu her bir olayda test etme yoluyla belirlemeniz gerekir. İki kod kümesi dikkatli bir şekilde koordine edilmemiş ve test edilmemişse beklenmedik sonuçlar elde edilebilir.

## <a name="call-vba-code-from-the-customization-assembly"></a>Özelleştirme derlemesi'nde VBA kodunu çağırma
 Word belgelerde makroları çağırabilirsiniz ve çalışma kitaplarında makroları ve işlevleri Excel çağırabilirsiniz. Bunu yapmak için aşağıdaki yöntemlerden birini kullanın:

- Word için sınıfının <xref:Microsoft.Office.Interop.Word._Application.Run%2A> yöntemini <xref:Microsoft.Office.Interop.Word.Application> çağırma.

- Daha Excel sınıfının yöntemini <xref:Microsoft.Office.Interop.Excel._Application.Run%2A> <xref:Microsoft.Office.Interop.Excel.Application> çağırma.

  Her yöntem için ilk parametre, çağrısı yapmak istediğiniz makronun veya işlevin adını tanımlar ve kalan isteğe bağlı parametreler makroya veya işleve geçecek parametreleri belirtir. İlk parametre, Word ve Excel için farklı biçimlere sahip olabilir:

- Word için ilk parametre şablon, modül ve makro adının herhangi bir birleşimini içeren bir dizedir. Belge adını belirtirsiniz, kodunuz yalnızca geçerli bağlamla ilgili belgelerde makrolar çalıştırabilir; herhangi bir belgede makro çalıştırabilir.

- Örneğin Excel parametre makro adını belirten bir dize, işlevin nerede olduğunu belirten bir dize veya kayıtlı DLL (XLL) işlevi için yazman <xref:Microsoft.Office.Interop.Excel.Range> kimliği olabilir. Bir dizeyi geçersiniz, dize etkin sayfa bağlamında değerlendirilir.

  Aşağıdaki kod örneğinde, belge düzeyi projeden adlı bir makronun çağrılarak nasıl `MyMacro` çağrıl Excel. Bu örnekte, içinde `MyMacro` tanımlandığı varsay varsaydır. `Sheet1`

```vb
Globals.Sheet1.Application.Run("MyMacro")
```

```csharp
Globals.Sheet1.Application.Run("MyMacro", missing, missing, missing,
    missing, missing, missing, missing, missing, missing, missing,
    missing, missing, missing, missing, missing, missing, missing,
    missing, missing, missing, missing, missing, missing, missing,
    missing, missing, missing, missing, missing, missing);
```

> [!NOTE]
> Visual C# içinde isteğe bağlı parametreler yerine genel değişkeni kullanma hakkında bilgi için bkz. Office `missing` [çözümlerinde kod yazma.](../vsto/writing-code-in-office-solutions.md)

## <a name="call-code-in-document-level-customizations-from-vba"></a>VBA'dan belge düzeyi özelleştirmelerde kod çağırma
 Belgede yer alan Visual Basic for Applications (VBA) kodunun özelleştirme derlemesinde kod çağıra Excel Word veya Excel için belge düzeyinde bir proje yapılandırabilirsiniz. Bu, aşağıdaki senaryolarda yararlıdır:

- Aynı belgeyle ilişkili belge düzeyinde özelleştirme özellikleri kullanarak bir belgede var olan VBA kodunu genişletmek istediğiniz.

- Belge düzeyinde özelleştirmeyle geliştirdiğiniz hizmetleri, belgeye VBA kodu yazarak hizmetlere erişen son kullanıcılar için kullanılabilir hale almak istiyorsanız.

  Office geliştirme araçları, Visual Studio için benzer bir özellik VSTO sağlar. Yeni bir Eklenti VSTO, diğer eklenti çözümlerinden VSTO eklentisinde kod Microsoft Office çağırabilirsiniz. Daha fazla bilgi için [bkz. Diğer VSTO çözümlerinden eklentilerde kod Office.](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)

> [!NOTE]
> Bu özellik Word şablonu projelerinde kullanılamaz. Yalnızca Word belgesinde, çalışma Excel veya şablon projelerinde Excel kullanılabilir.

## <a name="requirements"></a>Gereksinimler
 VBA kodunu özelleştirme derlemesine çağıracak şekilde etkinleştiremeden önce projenizin aşağıdaki gereksinimleri karşılaması gerekir:

- Belgenin aşağıdaki dosya adı uzantılarından biri olması gerekir:

  - Word için: *.docm* veya *.doc*

  - Daha Excel: *.xlsm*, *.xltm*, *.xls* veya *.xlt*

- Belgenin içinde VBA kodu olan bir VBA projesi zaten olması gerekir.

- Belgede yer alan VBA kodunun kullanıcıdan makroları etkinleştirmesi istenmeden çalışmasına izin verilmiyor. Word veya Office için Güven Merkezi ayarlarında güvenilir konumlar listesine Office VBA kodunun çalıştırılacağını Excel.

- Bu Office, VBA'da açığa çıkararak bir veya daha fazla ortak üye içeren en az bir genel sınıf içermesi gerekir.

     Yöntemleri, özellikleri ve olayları VBA'da ortaya çıkarabilirsiniz. Ortaya çıkarladığınız sınıf bir konak öğesi sınıfı (Word için veya Excel için gibi) veya projeniz içinde tanımladığınız `ThisDocument` `ThisWorkbook` başka bir sınıf `Sheet1` olabilir. Konak öğeleri hakkında daha fazla bilgi için bkz. [Konak öğelerine ve konak denetimlerine genel bakış.](../vsto/host-items-and-host-controls-overview.md)

## <a name="enable-vba-code-to-call-into-the-customization-assembly"></a>Özelleştirme derlemesine çağrı yapmak için VBA kodunu etkinleştirme
 Bir özelleştirme derlemesinde üyeleri belgede VBA koduna göstermek için iki farklı yol vardır:

- Bir proje içinde bir konak öğesi sınıfının üyelerini [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] VBA'da ortaya çıkarabilirsiniz. Bunu yapmak için, konak öğesi (belge, çalışma sayfası veya  çalışma kitabı) tasarımcıda açıkken Özellikler penceresinde konak öğesinin **EnableVbaCallers** özelliğini **True** olarak ayarlayın. Visual Studio VBA kodunun sınıf üyelerini çağıracağını etkinleştirmek için gereken tüm işi otomatik olarak gerçekleştirir.

- Visual C# projesinde herhangi bir genel sınıftaki üyeleri veya proje içinde konak olmayan bir öğe sınıfındaki üyeleri [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] VBA'ya sebilirsiniz. Bu seçenek, VBA'da hangi sınıfların açığa çıkarılacağını seçmeniz için size daha fazla serbestlik sağlar, ancak daha fazla el ile adım gerektirir.

   Bunu yapmak için aşağıdaki ana adımları gerçekleştirmeniz gerekir:

  1. Sınıfı COM'da ortaya çıkarır.

  2. VBA'ya açığa çıkararak sınıfın bir örneğini geri almak için projenizin konak öğesi sınıfının **GetAutomationObject** yöntemini geçersiz kılın.

  3. Projedeki **herhangi bir konak öğesi sınıfının ReferenceAssemblyFromVbaProject** özelliğini True olarak **ayarlayın.** Bu, özelleştirme derlemesi tür kitaplığını derlemeye ekler ve belgedeki VBA projesine tür kitaplığına bir başvuru ekler.

  Ayrıntılı yönergeler için bkz. Nasıl [yapılır: Bir Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md) projesinde kodu VBA'ya açığa çıkarma ve Nasıl yapılır: Visual C&#35; projesinde kodu [VBA'ya&#35;.](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)

  **EnableVbaCallers** ve **ReferenceAssemblyFromVbaProject** özellikleri yalnızca tasarım zamanında **Özellikler** penceresinde kullanılabilir; çalışma zamanında kullanılamaz. Özellikleri görüntülemek için, içinde bir konak öğesi için tasarımcıyı [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] açın. Bu özellikleri ayarlayacak belirli görevler Visual Studio daha fazla bilgi için bkz. Konak öğesi özellikleri tarafından [gerçekleştirilen görevler.](#PropertyTasks)

> [!NOTE]
> Çalışma kitabı veya belge zaten VBA kodu içeriyorsa veya belgedeki VBA kodunun çalışmasına güvenilmiyorsa **EnableVbaCallers** veya **ReferenceAssemblyFromVbaProject** özelliğini True olarak ayarsanız bir hata iletisi **alırsınız.** Bunun nedeni Visual Studio vbA projesini değiştirenin bu durumda değiştirileyemilmesidir.

## <a name="use-members-in-vba-code-to-call-into-the-customization-assembly"></a>Özelleştirme derlemesine çağrı yapmak için VBA kodundaki üyeleri kullanma
 Projenizi özelleştirme derlemesine çağrı yapmak üzere VBA kodunu etkinleştirecek şekilde yapılandırdıktan sonra, Visual Studio belgede VBA projesine aşağıdaki üyeleri ekler:

- Tüm projeler için Visual Studio adlı genel bir yöntem `GetManagedClass` ekler.

- [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] **EnableVbaCallers** özelliğini kullanarak bir konak öğesi sınıfının üyelerini açığa çıkararak projelerde, Visual Studio VBA projesinde , , , veya modülüne adlı bir özellik de `CallVSTOAssembly` `ThisDocument` `ThisWorkbook` `Sheet1` `Sheet2` `Sheet3` ekler.

  projesinde VBA koduna maruz kaldığın sınıfın genel `CallVSTOAssembly` `GetManagedClass` üyelerine erişmek için özelliğini veya yöntemini kullanabilirsiniz.

> [!NOTE]
> Çözümlerinizi geliştirirken ve dağıtırken, VBA kodunu ekleyebilirsiniz. Daha fazla bilgi için [bkz. Belgeye VBA kodu ekleme yönergeleri.](#Guidelines)

### <a name="use-the-callvstoassembly-property-in-a-visual-basic-project"></a>Visual Basic projesinde CallVSTOAssembly özelliğini kullanma
 Konak `CallVSTOAssembly` öğesi sınıfına ekleyiştirilen ortak üyelere erişmek için özelliğini kullanın. Örneğin, aşağıdaki VBA makrosu bir çalışma kitabı projesinin sınıfında `MyVSTOMethod` tanımlanan adlı Excel `Sheet1` çağıran.

```vb
Sub MyMacro()
    Sheet1.CallVSTOAssembly.MyVSTOMethod()
End Sub
```

 Bu özellik, doğrudan yöntemini kullanmak yerine özelleştirme derlemesine çağrı yapmak için daha kullanışlı `GetManagedClass` bir yöntemdir. `CallVSTOAssembly` , VBA'ya maruz kaldığın konak öğesi sınıfını temsil eden bir nesne döndürür. Döndürülen nesnenin üyeleri ve yöntem parametreleri IntelliSense'te görünür.

 `CallVSTOAssembly`özelliği, aşağıdaki koda benzer bir bildirime sahip. Bu kod, VBA'ya adlı bir çalışma kitabı `Sheet1` projesinde Excel öğe sınıfını açığa `ExcelWorkbook1` çıkarabilirsiniz.

```vb
Property Get CallVSTOAssembly() As ExcelWorkbook1.Sheet1
    Set CallVSTOAssembly = GetManagedClass(Me)
End Property
```

### <a name="use-the-getmanagedclass-method"></a>GetManagedClass yöntemini kullanma
 Genel yöntemi kullanmak `GetManagedClass` için **GetAutomationObject** yöntemini geçersiz kılmanızı içeren konak öğesi sınıfına karşılık gelen VBA nesnesini iletir. Ardından, VBA'da ortaya çıkararak sınıfa erişmek için döndürülen nesnesini kullanın.

 Örneğin, aşağıdaki VBA makrosu adlı bir çalışma kitabı projesinde konak öğesi sınıfında `MyVSTOMethod` tanımlanan adlı Excel yöntemini `Sheet1` `ExcelWorkbook1` çağıran.

```vb
Sub CallVSTOMethod
    Dim VSTOSheet1 As ExcelWorkbook1.Sheet1
    Set VSTOSheet1 = GetManagedClass(Sheet1)
    VSTOSheet1.MyVSTOMethod
End Sub
```

 yöntemi `GetManagedClass` aşağıdaki bildirime sahip.

```vb
GetManagedClass(pdispInteropObject Object) As Object
```

 Bu yöntem, VBA'ya maruz kaldığınızı sınıfını temsil eden bir nesne döndürür. Döndürülen nesnenin üyeleri ve yöntem parametreleri IntelliSense'te görünür.

## <a name="guidelines-for-adding-vba-code-to-the-document"></a><a name="Guidelines"></a> Belgeye VBA kodu ekleme yönergeleri
 Belge düzeyi özelleştirmeye çağrıda bulunduran VBA kodu ekleyebilirsiniz, belgenin birkaç farklı kopyası vardır.

 Çözüm geliştirmek ve test etmek için projenizin hata ayıklamasını ayıklar veya projenizi Visual Studio (derleme çıkış klasöründeki belge) sırasında açılan belgede VBA kodu yazabilirsiniz. Ancak projeyi bir sonraki derlemeniz sonrasında bu belgeye ekley istediğiniz VBA kodunun üzerine yazılacaktır çünkü Visual Studio derleme çıkış klasöründeki belgeyi ana proje klasöründeki belgenin bir kopyasıyla değiştirir.

 Çözümde hata ayıklama veya çalıştırma sırasında belgeye ekley istediğiniz VBA kodunu kaydetmek için VBA kodunu proje klasöründeki belgeye kopyalayın. Derleme işlemi hakkında daha fazla bilgi için bkz. [Office çözümleri oluşturma.](../vsto/building-office-solutions.md)

 Çözümlerinizi dağıtmaya hazır olduğunda, VBA kodunu ekleyebilirsiniz üç ana belge konumu vardır.

### <a name="in-the-project-folder-on-the-development-computer"></a>Geliştirme bilgisayarında proje klasöründe
 Belge ve özelleştirme kodunda hem VBA kodu üzerinde tam denetime sahip olursanız bu konum kullanışlıdır. Belge geliştirme bilgisayarda olduğundan, özelleştirme kodunu değiştirirken VBA kodunu kolayca değiştirebilirsiniz. Çözümlerinizi derleme, hata ayıklama ve yayımlamada belgenin bu kopyasına ekley istediğiniz VBA kodu belgede kalır.

 VBA kodunu tasarımcıda açıkken belgeye ekamazsınız. Önce tasarımcıda belgeyi kapatmanız ve sonra belgeyi doğrudan Word veya Excel.

> [!CAUTION]
> Belge açıldığında çalışan VBA kodu eklersiniz, nadir durumlarda bu kod belgeyi bozabilir veya tasarımcıda açılmasını önlenebilir.

### <a name="in-the-publish-or-installation-folder"></a>Yayımlama veya yükleme klasöründe
 Bazı durumlarda, VBA kodunu yayımla veya yükleme klasöründe belgeye eklemek uygun olabilir. Örneğin, VBA kodu yüklü yüklü değil bir bilgisayarda farklı bir geliştirici tarafından yazılmış ve test edilmişse bu Visual Studio seçebilirsiniz.

 Kullanıcılar çözümü doğrudan yayımlama klasöründen yüklemişse, çözümü her yayımlasanız VBA kodunu belgeye eklemeniz gerekir. Visual Studio yayımla konumdaki belgenin üzerine yazarak çözümü yayımlarsınız.

 Kullanıcılar çözümü yayımlama klasöründen farklı bir yükleme klasöründen yüklemişse, çözümü her yayımlasanız vbA kodunu belgeye eklemekten kaçınabilirsiniz. Yayımlama güncelleştirmesi yayımlama klasöründen yükleme klasörüne taşınmaya hazır olduğunda, tüm dosyaları belge dışında yükleme klasörüne kopyalayın.

### <a name="on-the-end-user-computer"></a>Son kullanıcı bilgisayarda
 Son kullanıcılar, belge düzeyi özelleştirmede sağlanmış hizmetlere çağrı yapan VBA geliştiricileri ise, belge kopyalarında özelliğini veya yöntemini kullanarak kodunuzu nasıl çağıracağını onlara `CallVSTOAssembly` `GetManagedClass` anlatabilirsiniz. Çözümün güncelleştirmelerini yayımlasanız, belge güncelleştirmeleri yayımlayan tarafından değiştirilmeytiği için son kullanıcı bilgisayarına belgede VBA kodunun üzerine yazılmaz.

## <a name="tasks-performed-by-the-host-item-properties"></a><a name="PropertyTasks"></a> Konak öğesi özellikleri tarafından gerçekleştirilen görevler
 **EnableVbaCallers** ve **ReferenceAssemblyFromVbaProject** özelliklerini kullanırken, Visual Studio görev kümeleri gerçekleştirir.

### <a name="enablevbacallers"></a>Enablevbacallers
 Bir konak öğesinin **EnableVbaCallers** özelliğini bir Visual Basic **projesinde True** olarak ayar Visual Studio görevleri gerçekleştirir:

1. Konak öğe <xref:Microsoft.VisualBasic.ComClassAttribute> <xref:System.Runtime.InteropServices.ComVisibleAttribute> sınıfına ve özniteliklerini ekler.

2. Konak öğe sınıfının **GetAutomationObject** yöntemini geçersiz kılar.

3. Konak öğesinin **ReferenceAssemblyFromVbaProject** özelliğini True olarak **ayarlar.**

   **EnableVbaCallers özelliğini** False olarak ayar Visual Studio aşağıdaki görevleri gerçekleştirir:

4. ve <xref:Microsoft.VisualBasic.ComClassAttribute> <xref:System.Runtime.InteropServices.ComVisibleAttribute> özniteliklerini sınıfından `ThisDocument` kaldırır.

5. **GetAutomationObject yöntemini** konak öğe sınıfından kaldırır.

   > [!NOTE]
   > Visual Studio **ReferenceAssemblyFromVbaProject** özelliğini otomatik olarak False olarak **ayarlamaz.** Özellikler penceresini kullanarak bu özelliği **el ile False** olarak **ayarlayın.**

### <a name="referenceassemblyfromvbaproject"></a>Referenceassemblyfromvbaproject
 bir Visual Basic veya Visual C# projesinde herhangi bir konak öğesinin **ReferenceAssemblyFromVbaProject** özelliği **True** olarak ayarlanırsa, Visual Studio görevleri gerçekleştirir:

1. Özelleştirme derlemesi için bir tür kitaplığı üretir ve tür kitaplığını derlemeye katıştırıyor.

2. Belgedeki VBA projesinde aşağıdaki tür kitaplıklarına bir başvuru ekler:

   - Özelleştirme derlemeniz için tür kitaplığı.

   - Office Yürütme Altyapısı 9.0 Tür Kitaplığı için Microsoft Visual Studio Araçları. Bu tür kitaplığı içinde yer [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] almaktadır.

   **ReferenceAssemblyFromVbaProject** özelliği **False** olarak yeniden ayarlanırsa Visual Studio görevleri gerçekleştirir:

3. Belgedeki VBA projesinden tür kitaplığı başvurularını kaldırır.

4. Katıştırılmış tür kitaplığını derlemeden kaldırır.

## <a name="troubleshoot"></a>Sorun giderme
 Aşağıdaki tabloda bazı yaygın hatalar ve hataları düzeltmeye yönelik öneriler listele türetir.

|Hata|Öneri|
|-----------|----------------|
|**EnableVbaCallers** veya **ReferenceAssemblyFromVbaProject** özelliğini ayardikten sonra, bir hata iletisi belgede VBA projesi olmadığını veya belgedeki VBA projesine erişim izniniz olmadığını gösterir.|Proje belgesinde en az bir VBA makrosu olduğundan, VBA projesinin çalıştırmak için yeterli güvene sahip olduğundan ve VBA projesinin parolayla korunmay olduğundan emin olun.|
|**EnableVbaCallers** veya **ReferenceAssemblyFromVbaProject** özelliğini ayardikten sonra, bir hata iletisi bildirimin eksik <xref:System.Runtime.InteropServices.GuidAttribute> veya bozuk olduğunu gösterir.|Bildirimin <xref:System.Runtime.InteropServices.GuidAttribute> projenizin *AssemblyInfo.cs* veya *AssemblyInfo.vb* dosyasında olduğundan ve bu özniteliğin geçerli bir GUID'ye ayarlanmış olduğundan emin olun.|
|**EnableVbaCallers** veya **ReferenceAssemblyFromVbaProject** özelliğini ayardikten sonra, bir hata iletisi tarafından belirtilen sürüm numarasının <xref:System.Reflection.AssemblyVersionAttribute> geçerli olmadığını gösterir.|Projenizin <xref:System.Reflection.AssemblyVersionAttribute> *AssemblyInfo.cs* veya *AssemblyInfo.vb* dosyasındaki bildirimin geçerli bir derleme sürüm numarasına ayarlanmış olduğundan emin olun. Geçerli derleme sürümü numaraları hakkında bilgi için sınıfına <xref:System.Reflection.AssemblyVersionAttribute> bakın.|
|Özelleştirme derlemesi yeniden adlandırıldıktan sonra, özelleştirme derlemesine çağıran VBA kodu çalışmayı durdurur.|Özelleştirme derlemesini VBA kodunda kullandıktan sonra değiştirirsanız, belgede VBA projesi ile özelleştirme derlemeniz arasındaki bağlantı bozuk olur. Bu sorunu düzeltmek için projenizin **ReferenceFromVbaAssembly** özelliğini **False** olarak değiştirin ve **ardından True** olarak değiştirin ve ARDıNDAN VBA kodundaki eski derleme adına yapılan tüm başvuruları yeni derleme adıyla değiştirin.|

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl olur: Visual Basic projesinde kodu VBA'Visual Basic açığa çıkarma](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)
- [Nasıl olur: Visual C çalışma grubu projesinde kodu VBA'&#35; açığa çıkarma](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)
- [Adım adım kılavuz: Visual Basic projesinde VBA'dan kod çağırma](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)
- [Adım adım kılavuz: Visual C çalışma grubu projesinde VBA'dan&#35; çağırma](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)
- [Yeni çözümler tasarlama Office oluşturma](../vsto/designing-and-creating-office-solutions.md)
- [Karşılaştırmalı olarak Office VBA Visual Studio çözümleri](../vsto/vba-and-office-solutions-in-visual-studio-compared.md)
- [Program belge düzeyi özelleştirmeleri](../vsto/programming-document-level-customizations.md)
