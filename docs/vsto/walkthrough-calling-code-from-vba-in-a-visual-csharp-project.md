---
title: "İzlenecek yol: Visual C# projesinde VBA 'dan kod çağırma"
description: çalışma kitabındaki Visual Basic for Applications (VBA) kodundan Microsoft Excel için belge düzeyi özelleştirmesindeki bir yöntemi çağırmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel [Office development in Visual Studio], calling code from VBA
- Word [Office development in Visual Studio], calling code from VBA
- Visual C# [Office development in Visual Studio], calling code from VBA
- workbooks [Office development in Visual Studio], calling code from VBA
- VBA [Office development in Visual Studio], calling code in document-level customizations
- Office documents [Office development in Visual Studio, Visual Basic for Applications and
- calling code from VBA
- document-level customizations [Office development in Visual Studio], calling code
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 1556eab077a56bc3b6880cc9a0a413e782f98c2d
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633782"
---
# <a name="walkthrough-call-code-from-vba-in-a-visual-c-project"></a>İzlenecek yol: Visual C# projesinde VBA 'dan kod çağırma
  bu izlenecek yol, çalışma kitabındaki Visual Basic for Applications (VBA) kodundan Microsoft Office Excel için belge düzeyi özelleştirmesinde bir yöntemin nasıl çağrılacağını gösterir. Yordamda üç temel adım vardır: konak öğesi sınıfına bir yöntem ekleyin `Sheet1` , yöntemi çalışma KITABıNDA VBA kodu olarak kullanıma sunun ve sonra çalışma KITABıNDAKI VBA kodundan yöntemi çağırın.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 bu izlenecek yol özellikle Excel kullanmasına karşın, izlenecek yol tarafından gösterilen kavramlar, Word için belge düzeyi projelerine da uygulanabilir.

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- VBA kodu içeren bir çalışma kitabı oluşturma.

- Excel içindeki güven merkezini kullanarak çalışma kitabının konumuna güvenme.

- `Sheet1`Konak öğesi sınıfına bir yöntem ekleme.

- Konak öğesi sınıfı için bir arabirim ayıklanıyor `Sheet1` .

- Yöntemi VBA koduna sunma.

- VBA kodundan yöntemi çağırma.

> [!NOTE]
> Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. daha fazla bilgi için bkz. [Visual Studio ıde 'yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Excel

## <a name="create-a-workbook-that-contains-vba-code"></a>VBA kodu içeren bir çalışma kitabı oluşturma
 İlk adım basit bir VBA makrosu içeren makro içerebilen bir çalışma kitabı oluşturmaktır. Bir özelleştirmesindeki kodu VBA 'da kullanıma sunmadan önce çalışma kitabında VBA kodu zaten bulunmalıdır. aksi takdirde, Visual Studio vba kodunu özelleştirme derlemesine çağırmak için vba projesini değiştiremez.

 Kullanmak istediğiniz VBA kodunu içeren bir çalışma kitabınız zaten varsa, bu adımı atlayabilirsiniz.

### <a name="to-create-a-workbook-that-contains-vba-code"></a>VBA kodu içeren bir çalışma kitabı oluşturmak için

1. Excel başlatın.

2. etkin belgeyi, **workbookwithvba** adlı bir **Excel Macro-Enabled çalışma kitabı ( \* . xlsm)** olarak kaydedin. Masaüstü gibi uygun bir konuma kaydedin.

3. Şeritte **Geliştirici** sekmesine tıklayın.

    > [!NOTE]
    > **Geliştirici** sekmesi görünür değilse, önce onu göstermelisiniz. Daha fazla bilgi için bkz. [nasıl yapılır: Şeritte Geliştirici sekmesini gösterme](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

4. **Kod** grubunda **Visual Basic**' a tıklayın.

     Visual Basic düzenleyicisi açılır.

5. **Project** penceresinde, **ThisWorkbook**' a çift tıklayın.

     Nesne için kod dosyası `ThisWorkbook` açılır.

6. Aşağıdaki VBA kodunu kod dosyasına ekleyin. Bu kod, hiçbir şey yapmaz bir basit işlevi tanımlar. Bu işlevin tek amacı, bir VBA projesinin çalışma kitabında mevcut olduğundan emin olmak içindir. Bu izlenecek yolda sonraki adımlar için bu gereklidir.

    ```vb
    Sub EmptySub()
    End Sub
    ```

7. Belgeyi kaydedin ve çıkış Excel.

## <a name="create-the-project"></a>Proje oluşturma
 artık, daha önce oluşturduğunuz makro özellikli çalışma kitabını kullanan Excel için belge düzeyi bir proje oluşturabilirsiniz.

### <a name="to-create-a-new-project"></a>Yeni bir proje oluşturmak için

1. Başlatın [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. **Dosya** menüsünde, **Yeni**' nin üzerine gelin ve **Project**' ye tıklayın.

3. şablonlar bölmesinde, **Visual C#**' ı genişletin ve ardından **Office/SharePoint**' ı genişletin.

4. **Office eklentileri** düğümünü seçin.

5. proje şablonları listesinde **Excel 2010 çalışma** kitabını veya **Excel 2013 çalışma kitabı** projesini seçin.

6. **Ad** kutusuna **CallingCodeFromVBA** yazın.

7. **Tamam**'a tıklayın.

     **Office için Visual Studio Araçları Project sihirbazı** açılır.

8. **Var olan bir belgeyi Kopyala**' yı seçin ve **var olan belgenin tam yolu** kutusunda, daha önce oluşturduğunuz **WorkbookWithVBA** çalışma kitabının konumunu belirtin. Makro içerebilen kendi çalışma kitabınızı kullanıyorsanız, onun yerine bu çalışma kitabının konumunu belirtin.

9. **Finish (Son)** düğmesine tıklayın.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]tasarımcıda **WorkbookWithVBA** çalışma kitabını açar ve **Çözüm Gezgini** Için **CallingCodeFromVBA** projesini ekler.

## <a name="trust-the-location-of-the-workbook"></a>Çalışma kitabının konumuna güvenin
 Çözümünüzdeki kodu çalışma kitabındaki VBA koduna göre açığa çıkarmak için önce çalışma kitabındaki VBA 'Yı çalıştırmak üzere güvenmelisiniz. Bunu yapmanın birkaç yolu vardır. Bu kılavuzda, Excel **güven merkezindeki** çalışma kitabının konumuna güvenerek bu görevi tamamlayacaksınız.

### <a name="to-trust-the-location-of-the-workbook"></a>Çalışma kitabının konumuna güvenmek için

1. Excel başlatın.

2. **Dosya** sekmesine tıklayın.

3. **Excel seçenekler** düğmesine tıklayın.

4. Kategoriler bölmesinde **Güven Merkezi**' ne tıklayın.

5. ayrıntılar bölmesinde **güven merkezi Ayarlar**' ne tıklayın.

6. Kategoriler bölmesinde, **Güvenilen konumlar**' a tıklayın.

7. Ayrıntılar bölmesinde, **Yeni Konum Ekle**' ye tıklayın.

8. **Microsoft Office güvenilir konum** iletişim kutusunda, **callingcodefromvba** projesini içeren klasöre gidin.

9. **Bu konumun alt klasörlerini seçin de güvenilirdir**.

10. **Microsoft Office güvenilir konum** iletişim kutusunda **tamam**' a tıklayın.

11. **Güven Merkezi** Iletişim kutusunda **Tamam**' a tıklayın.

12. **Excel seçenekleri** iletişim kutusunda **tamam**' a tıklayın.

13. Çıkış **Excel**.

## <a name="add-a-method-to-the-sheet1-class"></a>Sayfa1 sınıfına bir yöntem ekleyin
 Artık VBA projesi ayarlanmış olduğuna göre, `Sheet1` VBA kodundan çağırabilmeniz için konak öğesi sınıfına ortak bir yöntem ekleyin.

### <a name="to-add-a-method-to-the-sheet1-class"></a>Sayfa1 sınıfına bir yöntem eklemek için

1. **Çözüm Gezgini**, **Sheet1. cs** öğesine sağ tıklayın ve ardından **kodu görüntüle**' ye tıklayın.

     **Sheet1. cs** dosyası kod düzenleyicisinde açılır.

2. Aşağıdaki kodu `Sheet1` sınıfına ekleyin. `CreateVstoNamedRange`Yöntemi belirtilen aralıkta yeni bir <xref:Microsoft.Office.Tools.Excel.NamedRange> nesne oluşturur. Bu yöntem, olayı için bir olay işleyicisi de oluşturur <xref:Microsoft.Office.Tools.Excel.NamedRange.Selected> <xref:Microsoft.Office.Tools.Excel.NamedRange> . Bu izlenecek yolda daha sonra, `CreateVstoNamedRange` yöntemi BELGEDEKI VBA kodundan çağıracaksınız.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/CallingCodeFromVBA/Sheet1.cs" id="Snippet2":::

3. Sınıfına aşağıdaki yöntemi ekleyin `Sheet1` . Bu yöntem, <xref:Microsoft.Office.Tools.Excel.WorksheetBase.GetAutomationObject%2A> sınıfının geçerli örneğini döndürmek için yöntemini geçersiz kılar `Sheet1` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/CallingCodeFromVBA/Sheet1.cs" id="Snippet3":::

4. Sınıf bildiriminin ilk satırından önce aşağıdaki öznitelikleri uygulayın `Sheet1` . Bu öznitelikler sınıfı COM olarak görünür hale getirir, ancak bir sınıf arabirimi üretmeyecektir.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/CallingCodeFromVBA/Sheet1.cs" id="Snippet1":::

## <a name="extract-an-interface-for-the-sheet1-class"></a>Sheet1 sınıfı için bir arabirim Ayıkla
 Yöntemi VBA kodunda kullanıma sunmadan önce `CreateVstoNamedRange` , bu yöntemi tanımlayan bir ortak arabirim oluşturmanız ve bu ARABIRIMI com 'a almanız gerekir.

### <a name="to-extract-an-interface-for-the-sheet1-class"></a>Sheet1 sınıfına yönelik bir arabirim ayıklamak için

1. **Sheet1. cs** kod dosyasında, sınıfında herhangi bir yere tıklayın `Sheet1` .

2. Yeniden **Düzenle** menüsünde **Arabirimi Ayıkla**' ya tıklayın.

3. **Arabirimi Ayıkla** iletişim kutusunda, **arabirim oluşturmak Için ortak Üyeler seçin** kutusunda, yöntemi için girişe tıklayın `CreateVstoNamedRange` .

4. **Tamam**'a tıklayın.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] adlı yeni bir arabirim oluşturur `ISheet1` ve bu arabirimi `Sheet1` arabirimini uygulayan şekilde sınıfın tanımını değiştirir `ISheet1` . [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Ayrıca, kod Düzenleyicisi 'nde **ISheet1. cs** dosyasını açar.

5. **ISheet1. cs** dosyasında, `ISheet1` arabirim bildirimini aşağıdaki kodla değiştirin. Bu kod, `ISheet1` arabirimi genel hale getirir ve <xref:System.Runtime.InteropServices.ComVisibleAttribute> arabirimi com 'a görünür hale getirmek için özniteliğini uygular.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/CallingCodeFromVBA/ISheet1.cs" id="Snippet4":::

6. Projeyi derleyin.

## <a name="expose-the-method-to-vba-code"></a>Yöntemi VBA koduna sunun
 `CreateVstoNamedRange`Çalışma KITABıNDAKI VBA kodunda yöntemi göstermek için, konak öğesi Için **ReferenceAssemblyFromVbaProject** özelliğini `Sheet1` **true** olarak ayarlayın.

### <a name="to-expose-the-method-to-vba-code"></a>Yöntemi VBA koduna göstermek için

1. Içinde **Çözüm Gezgini,** **Sheet1.cs'ye çift tıklayın.**

     **WorkbookWithVBA dosyası** tasarımcıda açılır ve Sayfa1 görünür.

2. Özellikler **penceresinde** **ReferenceAssemblyFromVbaProject** özelliğini seçin ve değeri True olarak **değiştirin.**

3. Görüntülenen **iletide** Tamam'a tıklayın.

4. Projeyi derleyin.

## <a name="call-the-method-from-vba-code"></a>VBA kodundan yöntemini çağırma
 Artık çalışma kitabındaki `CreateVstoNamedRange` VBA kodundan yöntemini çağırabilirsiniz.

> [!NOTE]
> Bu kılavuzda, projede hata ayıklarken çalışma kitabına VBA kodu eksersiniz. Visual Studio, derleme çıktı klasöründeki belgeyi ana proje klasöründeki belgenin bir kopyasıyla değiştireceğini için, projeyi bir sonraki derlemesinde bu belgeye ekley istediğiniz VBA kodunun üzerine yazılır. VBA kodunu kaydetmek için proje klasöründeki belgeye kopyaabilirsiniz. Daha fazla bilgi için [bkz. VBA ve belge düzeyinde özelleştirmeleri birleştirme.](../vsto/combining-vba-and-document-level-customizations.md)

### <a name="to-call-the-method-from-vba-code"></a>VBA kodundan yöntemini çağırma

1. Projenizi **çalıştırmak için F5** tuşuna basın.

2. Geliştirici **sekmesinde,** Kod **grubunda,** Kod'a **Visual Basic.**

     Visual Basic Düzenleyicisi açılır.

3. Ekle menüsünde **Modül'e** **tıklayın.**

4. Aşağıdaki kodu yeni modüle ekleyin.

     Bu kod, özelleştirme `CreateTable` derlemesinde yöntemini arar. Makro, VBA koduna maruz kaldığın konak öğesi sınıfına erişmek için `GetManagedClass` genel yöntemini kullanarak bu `Sheet1` yönteme erişer. Bu `GetManagedClass` kılavuzda daha önce **ReferenceAssemblyFromVbaProject** özelliğini ayar her zaman yöntemi otomatik olarak oluşturulur.

    ```vb
    Sub CallVSTOMethod()
        Dim VSTOSheet1 As CallingCodeFromVBA.Sheet1
        Set VSTOSheet1 = GetManagedClass(Sheet1)
        Call VSTOSheet1.CreateVstoNamedRange(Sheet1.Range("A1"), "VstoNamedRange")
    End Sub
    ```

5. **F5 tuşuna basın.**

6. Açık çalışma kitabında, Sayfa1'de **A1 hücresine** **tıklayın.** İleti kutusunun görüntülendiğinden emin olmak.

7. Değişikliklerinizi Excel önce çıkış yapın.

## <a name="next-steps"></a>Sonraki adımlar
 VbA'dan kod çağırma hakkında daha fazla Office çözümlerini şu konulardan öğrenebilirsiniz:

- VBA'dan bir ana bilgisayar Visual Basic kodu çağırma. Bu işlem Visual C# işleminden farklıdır. Daha fazla bilgi için [bkz. Adım adım kılavuz: Bir projesinde VBA'dan Visual Basic çağırma.](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)

- VBA'dan VSTO bir eklentide kod çağırma. Daha fazla bilgi için bkz. Adım [adım: VBA'dan VSTO kod çağırma.](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)

## <a name="see-also"></a>Ayrıca bkz.
- [VBA ve belge düzeyi özelleştirmelerini birleştirme](../vsto/combining-vba-and-document-level-customizations.md)
- [Program belge düzeyi özelleştirmeleri](../vsto/programming-document-level-customizations.md)
- [Nasıl olur: Bir Visual Basic projesinde Kodu VBA'Visual Basic açığa çıkarma](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)
- [Nasıl yap: Visual C&#35; projesinde Kodu VBA'&#35; açığa çıkarma](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)
- [Adım adım kılavuz: Visual Basic projesinde VBA'dan kod çağırma](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)
