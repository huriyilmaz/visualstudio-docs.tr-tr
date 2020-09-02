---
title: VBA ve belge düzeyi özelleştirmelerini birleştirme
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b3bab9c132439c6efa53842f1e13c6c5be31db00
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "70977600"
---
# <a name="combine-vba-and-document-level-customizations"></a>VBA ve belge düzeyi özelleştirmelerini birleştirme
  Microsoft Office Word veya Microsoft Office Excel için belge düzeyi özelleştirmenin parçası olan bir belgede Visual Basic for Applications (VBA) kodunu kullanabilirsiniz. Özelleştirme derlemesinden belgedeki VBA kodunu çağırabilirsiniz veya özelleştirme derlemesindeki kodu çağırmak için projenizi belgedeki VBA kodunu etkinleştirecek şekilde yapılandırabilirsiniz.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="behavior-of-vba-code-in-a-document-level-customization"></a>Belge düzeyi özelleştirmesindeki VBA kodu davranışı
 Projenizi Visual Studio 'da açtığınızda, belge tasarım modunda açılır. Belge tasarım modundayken VBA kodu çalışmaz, bu nedenle VBA kodunu çalıştırmadan belge ve kod üzerinde çalışabilirsiniz.

 Çözümü çalıştırdığınızda hem VBA 'daki olay işleyicileri hem de özelleştirme derlemesi belgede oluşturulan olayları ve her iki kod çalıştırma kümesini seçer. Bundan önce hangi kodun çalıştırılacağını belirlenemez; her bireysel durumda test aracılığıyla bunu belirlemelisiniz. İki kod kümesi dikkatle koordine edilmez ve test edilmemiştir, beklenmeyen sonuçlar elde edebilirsiniz.

## <a name="call-vba-code-from-the-customization-assembly"></a>Özelleştirme derlemesinden VBA kodunu çağırma
 Word belgelerindeki makroları çağırabilirsiniz ve Excel çalışma kitaplarında makro ve işlevleri çağırabilirsiniz. Bunu yapmak için aşağıdaki yöntemlerden birini kullanın:

- Word için, <xref:Microsoft.Office.Interop.Word._Application.Run%2A> sınıfının yöntemini çağırın <xref:Microsoft.Office.Interop.Word.Application> .

- Excel için, <xref:Microsoft.Office.Interop.Excel._Application.Run%2A> sınıfının yöntemini çağırın <xref:Microsoft.Office.Interop.Excel.Application> .

  Her yöntem için, ilk parametre çağırmak istediğiniz makro veya işlevin adını tanımlar ve kalan isteğe bağlı parametreler, makroya veya işleve geçirilecek parametreleri belirtir. İlk parametre Word ve Excel için farklı biçimlere sahip olabilir:

- Word için ilk parametre, şablon, modül ve makro adının herhangi bir birleşimi olabilecek bir dizedir. Belge adını belirtirseniz, kodunuz yalnızca herhangi bir makro değil yalnızca geçerli içerikle ilgili belgelerde makro çalıştırabilir.

- Excel için ilk parametre, makro adını belirten bir dize olabilir, <xref:Microsoft.Office.Interop.Excel.Range> Bu, işlevin nerede olduğunu veya KAYıTLı dll (XLL) işlevi için bir kayıt kimliği olduğunu gösterir. Bir dize geçirirseniz, dize etkin sayfa bağlamında değerlendirilir.

  Aşağıdaki kod örneği, `MyMacro` Excel için belge düzeyindeki bir projeden adlı bir makronun nasıl çağrılacağını gösterir. Bu örnekte `MyMacro` , içinde tanımlanan varsayılır `Sheet1` .

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
> `missing`Visual C# ' de isteğe bağlı parametrelerin yerine genel değişkeni kullanma hakkında daha fazla bilgi için bkz. [Office çözümlerinde kod yazma](../vsto/writing-code-in-office-solutions.md).

## <a name="call-code-in-document-level-customizations-from-vba"></a>VBA 'daki belge düzeyi özelleştirmelerde kodu çağırma
 Word veya Excel için belge düzeyi projesi yapılandırarak belgedeki Visual Basic for Applications (VBA) kodu, özelleştirme derlemesindeki kodu çağırabilir. Bu, aşağıdaki senaryolarda yararlı olur:

- Belgedeki mevcut VBA kodunu, aynı belgeyle ilişkili belge düzeyi özelleştirmesindeki özellikler kullanarak genişletmek istiyorsunuz.

- Belge düzeyi özelleştirmesinde geliştirdiğiniz Hizmetleri, belgeye VBA kodu yazarak hizmetlere erişebilen son kullanıcılar için kullanılabilir hale getirmek istiyorsunuz.

  Visual Studio 'daki Office geliştirme araçları, VSTO eklentileri için benzer bir özellik sağlar. VSTO eklentisi geliştiriyorsanız, diğer Microsoft Office çözümlerdeki VSTO eklentiinizdeki kodu çağırabilirsiniz. Daha fazla bilgi için bkz. [VSTO eklentilerindeki kodu diğer Office Çözümlerinden çağırma](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).

> [!NOTE]
> Bu özellik Word şablon projelerinde kullanılamaz. Yalnızca Word belgesi, Excel çalışma kitabı veya Excel şablon projelerinde kullanılabilir.

## <a name="requirements"></a>Gereksinimler
 VBA kodunu özelleştirme derlemesine çağırmak üzere etkinleştirebilmeniz için, projenizin aşağıdaki gereksinimleri karşılaması gerekir:

- Belge aşağıdaki dosya adı uzantılarından birine sahip olmalıdır:

  - Word için: *. docm* veya *. doc*

  - Excel için: *. xlsm*, *. xltm*, *. xls*veya *. xlt*

- Belge, zaten VBA kodu olan bir VBA projesi içermelidir.

- Belgedeki VBA kodunun, kullanıcıdan makroları etkinleştirmesini istemeden çalışmasına izin verilmelidir. Office projesinin konumunu, Word veya Excel için Güven Merkezi ayarlarındaki güvenilir konumlar listesine ekleyerek çalıştırmak için VBA koduna güvenebilirsiniz.

- Office projesi, VBA 'da kullanıma sunan bir veya daha fazla ortak üye içeren en az bir ortak sınıf içermelidir.

     Yöntemleri, özellikleri ve olayları VBA 'da kullanıma sunabilirsiniz. Sergiledığınız sınıf, bir ana bilgisayar öğe sınıfı (örneğin `ThisDocument` , Word veya `ThisWorkbook` `Sheet1` Excel için) ya da projenizde tanımladığınız başka bir sınıf olabilir. Konak öğeleri hakkında daha fazla bilgi için bkz. [konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md).

## <a name="enable-vba-code-to-call-into-the-customization-assembly"></a>Özelleştirme derlemesine çağrı yapmak için VBA kodunu etkinleştirin
 Özelleştirme derlemesinde üyeleri belgedeki VBA koduna göre açığa çıkarmak için iki farklı yol vardır:

- Bir projedeki konak öğesi sınıfının üyelerini VBA 'da kullanıma sunabilirsiniz [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] . Bunu yapmak için, konak öğesi (yani belge, çalışma sayfası veya çalışma kitabı) tasarımcıda açıkken, konak öğesinin **EnableVbaCallers** özelliğini **Özellikler** penceresinde **true** olarak ayarlayın. Visual Studio, VBA kodunun sınıf üyelerini çağırmasını sağlamak için gereken tüm işleri otomatik olarak gerçekleştirir.

- Bir Visual C# projesindeki tüm ortak sınıftaki üyeleri veya bir projedeki konak olmayan öğe sınıfının üyelerini [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] VBA olarak ortaya çıkarmak için kullanabilirsiniz. Bu seçenek, VBA 'da hangi sınıfların kullanıma sunabileceğiniz hakkında daha fazla özgürlük sağlar, ancak aynı zamanda daha el ile adım gerektirir.

   Bunu yapmak için aşağıdaki ana adımları gerçekleştirmeniz gerekir:

  1. Sınıfı COM 'a sunun.

  2. VBA 'da kullanıma sunmanıza yardımcı olan sınıfın bir örneğini döndürmek için projenizdeki bir konak öğesi sınıfının **GetAutomationObject** yöntemini geçersiz kılın.

  3. Projedeki herhangi bir konak öğesi sınıfının **ReferenceAssemblyFromVbaProject** özelliğini **true**olarak ayarlayın. Bu, özelleştirme derlemesinin tür kitaplığını derlemeye gömer ve tür kitaplığına belgedeki VBA projesine bir başvuru ekler.

  Ayrıntılı yönergeler için bkz. [nasıl yapılır: bir Visual Basic projesindeki kodu VBA 'de kullanıma](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md) sunma ve [Visual C&#35; projesinde kodu VBA 'de kullanıma](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)sunma.

  **EnableVbaCallers** ve **ReferenceAssemblyFromVbaProject** özellikleri yalnızca tasarım zamanında **Özellikler** penceresinde kullanılabilir; çalışma zamanında kullanılamaz. Özellikleri görüntülemek için, içindeki bir konak öğesinin tasarımcısını açın [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Bu özellikleri ayarladığınızda Visual Studio 'Nun gerçekleştirdiği belirli görevler hakkında daha fazla bilgi için, bkz. [konak öğesi özellikleri tarafından gerçekleştirilen görevler](#PropertyTasks).

> [!NOTE]
> Çalışma kitabı veya belge zaten VBA kodu içermiyorsa veya belgedeki VBA kodu çalıştırılmak üzere güvenilmiyorsa, **EnableVbaCallers** veya **ReferenceAssemblyFromVbaProject** özelliğini **true**olarak ayarladığınızda bir hata iletisi alırsınız. Bunun nedeni, Visual Studio 'Nun belgedeki VBA projesini değiştiremeyeceği durumdur.

## <a name="use-members-in-vba-code-to-call-into-the-customization-assembly"></a>Özelleştirme derlemesine çağırmak için VBA kodundaki üyeleri kullanma
 Projenizi VBA kodunun özelleştirme derlemesine çağırmasını sağlayacak şekilde yapılandırdıktan sonra, Visual Studio aşağıdaki üyeleri belgedeki VBA projesine ekler:

- Tüm projeler için, Visual Studio adlı genel bir yöntem ekler `GetManagedClass` .

- [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]Bir konak öğesi sınıfının üyelerini **EnableVbaCallers** özelliğini kullanarak kullanıma sunabileceğiniz projeler için, Visual Studio `CallVSTOAssembly` `ThisDocument` VBA projesindeki,,, `ThisWorkbook` `Sheet1` `Sheet2` veya `Sheet3` modülüne adlı bir özellik de ekler.

  `CallVSTOAssembly` `GetManagedClass` Projedeki VBA koduna açık olan sınıfın ortak üyelerine erişmek için özelliğini veya yöntemini kullanabilirsiniz.

> [!NOTE]
> Çözümünüzü geliştirip dağıtırken, belgenin VBA kodunu ekleyebileceğiniz birkaç farklı kopyası vardır. Daha fazla bilgi için bkz. [belgeye VBA kodu eklemek Için yönergeler](#Guidelines).

### <a name="use-the-callvstoassembly-property-in-a-visual-basic-project"></a>Visual Basic projesindeki CallVSTOAssembly özelliğini kullanma
 `CallVSTOAssembly`Konak öğesi sınıfına eklediğiniz ortak üyelere erişmek için özelliğini kullanın. Örneğin, aşağıdaki VBA makrosu, `MyVSTOMethod` `Sheet1` bir Excel çalışma kitabı projesindeki sınıfında tanımlanmış adlı bir yöntemi çağırır.

```vb
Sub MyMacro()
    Sheet1.CallVSTOAssembly.MyVSTOMethod()
End Sub
```

 Bu özellik, yöntemi doğrudan kullanmaktan daha kolay bir şekilde özelleştirme derlemesini çağırmak için daha uygun bir yoldur `GetManagedClass` . `CallVSTOAssembly` VBA 'da kullanıma sunulan konak öğesi sınıfını temsil eden bir nesne döndürür. Döndürülen nesnenin Üyeler ve Yöntem parametreleri IntelliSense 'de görüntülenir.

 `CallVSTOAssembly`Özelliği aşağıdaki koda benzer bir bildirime sahiptir. Bu kod, `Sheet1` konak öğesi SıNıFıNı VBA adlı bir Excel çalışma kitabı projesinde kullanıma aldığını varsayar `ExcelWorkbook1` .

```vb
Property Get CallVSTOAssembly() As ExcelWorkbook1.Sheet1
    Set CallVSTOAssembly = GetManagedClass(Me)
End Property
```

### <a name="use-the-getmanagedclass-method"></a>GetManagedClass metodunu kullanın
 Genel yöntemi kullanmak için `GetManagedClass` , **GetAutomationObject** yönteminin geçersiz kılmasını içeren konak öğesi SıNıFıNA karşılık gelen VBA nesnesini geçirin. Ardından, VBA 'da kullanıma sunulan sınıfa erişmek için döndürülen nesneyi kullanın.

 Örneğin, aşağıdaki VBA makrosu adlı bir `MyVSTOMethod` `Sheet1` Excel çalışma kitabı projesindeki konak öğesi sınıfında tanımlanmış adlı bir yöntemi çağırır `ExcelWorkbook1` .

```vb
Sub CallVSTOMethod
    Dim VSTOSheet1 As ExcelWorkbook1.Sheet1
    Set VSTOSheet1 = GetManagedClass(Sheet1)
    VSTOSheet1.MyVSTOMethod
End Sub
```

 `GetManagedClass`Yönteminde aşağıdaki bildirim bulunur.

```vb
GetManagedClass(pdispInteropObject Object) As Object
```

 Bu yöntem, VBA 'da kullanıma sunulan sınıfı temsil eden bir nesne döndürür. Döndürülen nesnenin Üyeler ve Yöntem parametreleri IntelliSense 'de görüntülenir.

## <a name="guidelines-for-adding-vba-code-to-the-document"></a><a name="Guidelines"></a> Belgeye VBA kodu ekleme yönergeleri
 Belge düzeyi özelleştirmesine çağıran VBA kodunu ekleyebileceğiniz belgenin birçok farklı kopyası vardır.

 Çözümünüzü geliştirip test ederken, Visual Studio 'da (yani, derleme çıkış klasöründeki belge) hata ayıklarken veya projenizi çalıştırırken açılan belgeye VBA kodu yazabilirsiniz. Ancak, bu belgeye eklediğiniz tüm VBA kodları, projeyi bir sonraki sefer oluşturduğunuzda üzerine yazılır, çünkü Visual Studio derleme çıktı klasöründeki belgeyi ana proje klasöründen belgenin bir kopyasıyla değiştirir.

 Hata ayıklarken veya çözümü çalıştırırken belgeye eklediğiniz VBA kodunu kaydetmek istiyorsanız, VBA kodunu proje klasöründeki belgeye kopyalayın. Yapı işlemi hakkında daha fazla bilgi için bkz. [Build Office Solutions](../vsto/building-office-solutions.md).

 Çözümünüzü dağıtmaya hazırsanız, VBA kodunu ekleyebileceğiniz üç ana belge konumu vardır.

### <a name="in-the-project-folder-on-the-development-computer"></a>Geliştirme bilgisayarındaki proje klasöründe
 Belgedeki hem VBA kodunda hem de özelleştirme kodunda denetim tamamen varsa, bu konum kullanışlıdır. Belge geliştirme bilgisayarında olduğundan, özelleştirme kodunu değiştirirseniz VBA kodunu kolayca değiştirebilirsiniz. Belge kopyasının bu kopyasına eklediğiniz VBA kodu, çözümünüzü oluştururken, hata ayıkladığınızda ve yayımladığınızda belge içinde kalır.

 VBA kodunu, tasarımcıda açıkken belgeye ekleyemezsiniz. Önce tasarımcıda belgeyi kapatmanız ve belgeyi doğrudan Word veya Excel 'de açmanız gerekir.

> [!CAUTION]
> Belge açıldığında çalışan VBA kodunu eklerseniz, nadir olarak bu kod belgeyi bozabilir veya tasarımcıda açılmasını engelleyebilir.

### <a name="in-the-publish-or-installation-folder"></a>Yayımla veya yükleme klasöründe
 Bazı durumlarda, VBA kodunu Yayımla veya yükleme klasöründeki belgeye eklemek uygun olabilir. Örneğin, VBA kodu, Visual Studio yüklü olmayan bir bilgisayarda farklı bir geliştirici tarafından yazılmışsa ve test edildiğinde bu seçeneği belirleyebilirsiniz.

 Kullanıcılar çözümü doğrudan Yayımla klasöründen yüklerse, çözümü her yayımlamanızda VBA kodunu belgeye eklemeniz gerekir. Çözümü yayımladığınızda, Visual Studio Publish konumundaki belgenin üzerine yazar.

 Kullanıcılar çözümü yayımlama klasöründen farklı bir yükleme klasöründen yüklerse, çözümü her yayımladığınızda belgeye VBA kodunu eklemekten kaçınabilirsiniz. Yayımla klasöründen yükleme klasörüne taşımaya hazırsa, tüm dosyaları belge hariç yükleme klasörüne kopyalayın...

### <a name="on-the-end-user-computer"></a>Son Kullanıcı bilgisayarında
 Son kullanıcılar, belge düzeyi özelleştirmesinde sağladığınız hizmetlere çağıran VBA geliştiricilerindedir, `CallVSTOAssembly` özelliği veya belge kopyalarında metodunu kullanarak kodunuzun nasıl çağrılacağını söyleyebilirsiniz `GetManagedClass` . Güncelleştirmeleri çözümde yayımladığınızda, belge yayımlama güncelleştirmeleri tarafından değiştirilmediği için son kullanıcı bilgisayarındaki belgedeki VBA kodunun üzerine yazılmaz.

## <a name="tasks-performed-by-the-host-item-properties"></a><a name="PropertyTasks"></a> Konak öğesi özellikleri tarafından gerçekleştirilen görevler
 **EnableVbaCallers** ve **ReferenceAssemblyFromVbaProject** özelliklerini kullandığınızda, Visual Studio farklı görev kümeleri gerçekleştirir.

### <a name="enablevbacallers"></a>EnableVbaCallers
 Bir konak öğesinin **EnableVbaCallers** özelliğini bir Visual Basic projesinde **true** olarak ayarlarsanız, Visual Studio aşağıdaki görevleri gerçekleştirir:

1. , <xref:Microsoft.VisualBasic.ComClassAttribute> Ve <xref:System.Runtime.InteropServices.ComVisibleAttribute> özniteliklerini konak öğesi sınıfına ekler.

2. Konak öğesi sınıfının **GetAutomationObject** yöntemini geçersiz kılar.

3. Konak öğesinin **ReferenceAssemblyFromVbaProject** özelliğini **true**olarak ayarlar.

   **EnableVbaCallers** özelliğini **false**olarak belirlediğinizde, Visual Studio aşağıdaki görevleri gerçekleştirir:

4. <xref:Microsoft.VisualBasic.ComClassAttribute>Sınıfından ve özniteliklerini kaldırır <xref:System.Runtime.InteropServices.ComVisibleAttribute> `ThisDocument` .

5. **GetAutomationObject** metodunu konak öğesi sınıfından kaldırır.

   > [!NOTE]
   > Visual Studio, **ReferenceAssemblyFromVbaProject** özelliğini otomatik olarak **false**olarak ayarladı. Bu özelliği, **Özellikler** penceresini kullanarak el ile **false** olarak ayarlayabilirsiniz.

### <a name="referenceassemblyfromvbaproject"></a>ReferenceAssemblyFromVbaProject
 Bir Visual Basic veya Visual C# projesindeki herhangi bir konak öğesinin **ReferenceAssemblyFromVbaProject** özelliği **true**olarak ayarlandığında, Visual Studio aşağıdaki görevleri gerçekleştirir:

1. Özelleştirme derlemesi için bir tür kitaplığı oluşturur ve tür kitaplığını derlemeye gömer.

2. Belgedeki VBA projesinde aşağıdaki tür kitaplıklarına bir başvuru ekler:

   - Özelleştirme derlemelerinizin tür kitaplığı.

   - Office yürütme altyapısı 9,0 tür kitaplığı için Microsoft Visual Studio Araçları. Bu tür kitaplığı öğesine dahil edilmiştir [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .

   **ReferenceAssemblyFromVbaProject** özelliği **false**olarak ayarlandığında, Visual Studio aşağıdaki görevleri gerçekleştirir:

3. Belgedeki VBA projesinden tür kitaplığı başvurularını kaldırır.

4. Gömülü tür kitaplığını derlemeden kaldırır.

## <a name="troubleshoot"></a>Sorun giderme
 Aşağıdaki tabloda, hataları düzeltmek için bazı yaygın hatalar ve öneriler listelenmektedir.

|Hata|Öneri|
|-----------|----------------|
|**EnableVbaCallers** veya **ReferenceAssemblyFromVbaProject** özelliğini ayarladıktan sonra, bir hata iletisi belgenin bir VBA PROJESI içermediğini veya belgedeki VBA projesine erişim izniniz olduğunu belirtir.|Projedeki belgenin en az bir VBA makrosu içerdiğinden, VBA projesinde çalıştırmak için yeterli güven olduğundan ve VBA projesinin bir parolayla korunmadığından emin olun.|
|**EnableVbaCallers** veya **ReferenceAssemblyFromVbaProject** özelliğini ayarladıktan sonra, bir hata iletisi <xref:System.Runtime.InteropServices.GuidAttribute> bildirimin eksik veya bozuk olduğunu bildirir.|<xref:System.Runtime.InteropServices.GuidAttribute>Bildirimin, projenizdeki *AssemblyInfo.cs* veya *AssemblyInfo. vb* dosyasında bulunduğundan ve bu özniteliğin geçerli bir GUID 'ye ayarlandığından emin olun.|
|**EnableVbaCallers** veya **ReferenceAssemblyFromVbaProject** özelliğini ayarladıktan sonra, bir hata iletisi tarafından belirtilen sürüm numarasının <xref:System.Reflection.AssemblyVersionAttribute> geçerli olmadığı belirtilir.|<xref:System.Reflection.AssemblyVersionAttribute>Projenizdeki *AssemblyInfo.cs* veya *AssemblyInfo. vb* dosyasındaki bildirimin geçerli bir derleme sürüm numarası olarak ayarlandığından emin olun. Geçerli derleme sürüm numaraları hakkında daha fazla bilgi için, <xref:System.Reflection.AssemblyVersionAttribute> sınıfına bakın.|
|Özelleştirme derlemesini yeniden adlandırdıktan sonra, özelleştirme derlemesine çağıran VBA kodu çalışmayı durduruyor.|Özelleştirme derlemesinin adını VBA kodunda kullanıma aldıktan sonra değiştirirseniz, belgedeki VBA projesi ve Özelleştirme derlemeniz arasındaki bağlantı bozulur. Bu sorunu onarmak için, projenizdeki **ReferenceFromVbaAssembly** özelliğini **false** olarak değiştirin ve ardından **true**değerine dönün ve ardından VBA kodundaki eski derleme adına yapılan başvuruları yeni derleme adıyla değiştirin.|

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: Visual Basic projesindeki kodu VBA 'de kullanıma sunma](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)
- [Nasıl yapılır: Visual C&#35; projesinde kodu VBA 'de kullanıma sunma](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)
- [İzlenecek yol: Visual Basic projesindeki VBA 'dan kod çağırma](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)
- [İzlenecek yol: Visual C&#35; projesindeki VBA 'dan kod çağırma](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)
- [Office çözümleri tasarlama ve oluşturma](../vsto/designing-and-creating-office-solutions.md)
- [Visual Studio 'da VBA ve Office çözümleri karşılaştırması](../vsto/vba-and-office-solutions-in-visual-studio-compared.md)
- [Program belge düzeyi özelleştirmeleri](../vsto/programming-document-level-customizations.md)
