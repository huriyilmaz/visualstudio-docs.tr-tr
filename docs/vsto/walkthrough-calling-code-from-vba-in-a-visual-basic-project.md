---
title: "izlenecek yol: Visual Basic projesindeki VBA 'dan kod çağırma"
description: belgedeki Visual Basic for Applications (VBA) kodundan Microsoft Word için belge düzeyi özelleştirmesindeki bir yöntemi çağırmayı öğrenin.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], Visual Basic for Applications and
- ThisDocument class
- Word [Office development in Visual Studio], calling code from VBA
- Visual Basic [Office development in Visual Studio], calling code from VBA
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
ms.openlocfilehash: 631511ba470b42d07878d175c953bb7047914fc2
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633790"
---
# <a name="walkthrough-call-code-from-vba-in-a-visual-basic-project"></a>izlenecek yol: Visual Basic projesindeki VBA 'dan kod çağırma
  bu izlenecek yol, belgedeki Visual Basic for Applications (VBA) kodundan Microsoft Office Word için belge düzeyi özelleştirmesinde bir yöntemin nasıl çağrılacağını gösterir. Yordamda üç temel adım vardır: konak öğesi sınıfına bir yöntem ekleyin `ThisDocument` , YÖNTEMI VBA koduna sunun ve sonra BELGEDEKI VBA kodundan yöntemi çağırın.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Bu izlenecek yol, sözcüğü özel olarak kullanıyor olsa da, izlenecek yol tarafından gösterilen kavramlar Excel belge düzeyi projelere de uygulanır.

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- VBA kodu içeren bir belge oluşturuluyor.

- Word 'de güven merkezini kullanarak belgenin konumuna güvenme.

- `ThisDocument`Konak öğesi sınıfına bir yöntem ekleme.

- Yöntemi VBA koduna sunma.

- VBA kodundan yöntemi çağırma.

> [!NOTE]
> Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. daha fazla bilgi için bkz. [Visual Studio ıde 'yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word

## <a name="create-a-document-that-contains-vba-code"></a>VBA kodu içeren bir belge oluştur
 İlk adım basit bir VBA makrosu içeren makro içerebilen bir belge oluşturmaktır. belge, bu belgeye dayalı bir Visual Studio projesi oluşturmadan önce bir VBA projesi içermelidir. aksi takdirde, Visual Studio vba kodunu özelleştirme derlemesine çağırmak için vba projesini değiştiremez.

 Kullanmak istediğiniz VBA kodunu içeren bir belgeniz zaten varsa, bu adımı atlayabilirsiniz.

### <a name="to-create-a-document-that-contains-vba-code"></a>VBA kodu içeren bir belge oluşturmak için

1. Word 'Ü başlatın.

2. Etkin belgeyi makro içerebilen bir **belge ( \* . docm)** olarak **DocumentWithVBA** adlı bir belge olarak kaydedin. Masaüstü gibi uygun bir konuma kaydedin.

3. Şeritte **Geliştirici** sekmesine tıklayın.

    > [!NOTE]
    > **Geliştirici** sekmesi görünür değilse, önce onu göstermelisiniz. Daha fazla bilgi için bkz. [nasıl yapılır: Şeritte Geliştirici sekmesini gösterme](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

4. **Kod** grubunda **Visual Basic**' a tıklayın.

     Visual Basic düzenleyicisi açılır.

5. **Project** penceresinde **ThisDocument**' ye çift tıklayın.

     Nesne için kod dosyası `ThisDocument` açılır.

6. Aşağıdaki VBA kodunu kod dosyasına ekleyin. Bu kod, hiçbir şey yapmaz bir basit işlevi tanımlar. Bu işlevin tek amacı, bir VBA projesinin belgede mevcut olmasını sağlamaktır. Bu izlenecek yolda sonraki adımlar için bu gereklidir.

    ```vb
    Sub EmptySub()
    End Sub
    ```

7. Belgeyi kaydedin ve Word 'den çıkın.

## <a name="create-the-project"></a>Proje oluşturma
 Artık, daha önce oluşturduğunuz makro içerebilen belgeyi kullanan Word için belge düzeyi bir proje oluşturabilirsiniz.

### <a name="to-create-a-new-project"></a>Yeni bir proje oluşturmak için

1. Başlatın [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. **Dosya** menüsünde, **Yeni**' nin üzerine gelin ve **Project**' ye tıklayın. ıde 'niz Visual Basic geliştirme ayarlarını kullanacak şekilde ayarlandıysa, **dosya** menüsünde **yeni Project**' ye tıklayın.

3. şablonlar bölmesinde **Visual Basic**' ı genişletin ve **Office/SharePoint**' ı genişletin.

4. **Office eklentileri** düğümünü seçin.

5. Proje şablonları listesinde, **word 2010 belgesi** veya **Word 2013 belge** projesi ' ni seçin.

6. **Ad** kutusuna **CallingCodeFromVBA** yazın.

7. **Tamam**'a tıklayın.

     **Office için Visual Studio Araçları Project sihirbazı** açılır.

8. **Var olan bir belgeyi Kopyala**' yı seçin ve **var olan belgenin tam yolu** kutusunda, daha önce oluşturduğunuz **DocumentWithVBA** belgesinin konumunu belirtin. Makro içerebilen kendi belgenizi kullanıyorsanız, bunun yerine bu belgenin konumunu belirtin.

9. **Finish (Son)** düğmesine tıklayın.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]tasarımcıda **DocumentWithVBA** belgesini açar ve **Çözüm Gezgini** Için **CallingCodeFromVBA** projesini ekler.

## <a name="trust-the-location-of-the-document"></a>Belgenin konumuna güven
 Çözümünüzdeki kodu belgedeki VBA kodunda kullanıma sunmadan önce, çalıştırmak için belgede VBA 'ya güvenmelisiniz. Bunu yapmanın birkaç yolu vardır. Bu anlatım için, Word 'de **Güven Merkezi** 'nde belgenin konumuna güvenin.

### <a name="to-trust-the-location-of-the-document"></a>Belgenin konumuna güvenmek için

1. Word 'Ü başlatın.

2. **Dosya** sekmesine tıklayın.

3. **Word seçenekleri** düğmesine tıklayın.

4. Kategoriler bölmesinde **Güven Merkezi**' ne tıklayın.

5. ayrıntılar bölmesinde **güven merkezi Ayarlar**' ne tıklayın.

6. Kategoriler bölmesinde, **Güvenilen konumlar**' a tıklayın.

7. Ayrıntılar bölmesinde, **Yeni Konum Ekle**' ye tıklayın.

8. **Microsoft Office güvenilir konum** iletişim kutusunda, **callingcodefromvba** projesini içeren klasöre gidin.

9. **Bu konumun alt klasörlerini seçin de güvenilirdir**.

10. **Microsoft Office güvenilir konum** iletişim kutusunda **tamam**' a tıklayın.

11. **Güven Merkezi** Iletişim kutusunda **Tamam**' a tıklayın.

12. **Word seçenekleri** Iletişim kutusunda **Tamam**' a tıklayın.

13. Word 'den çık.

## <a name="add-a-method-to-the-thisdocument-class"></a>ThisDocument sınıfına bir yöntem ekleyin
 Artık VBA projesi ayarlanmış olduğuna göre, `ThisDocument` VBA kodundan çağırabilmeniz için konak öğesi sınıfına bir yöntem ekleyin.

### <a name="to-add-a-method-to-the-thisdocument-class"></a>ThisDocument sınıfına bir yöntem eklemek için

1. **Çözüm Gezgini**, **ThisDocument. vb** öğesine sağ tıklayın ve ardından **kodu görüntüle**' ye tıklayın.

     **ThisDocument. vb** dosyası kod düzenleyicisinde açılır.

2. Sınıfına aşağıdaki yöntemi ekleyin `ThisDocument` . Bu yöntem, belgenin başlangıcında iki satır ve iki sütun içeren bir tablo oluşturur. Parametreler, ilk satırda görüntülenen metni belirtir. Bu izlenecek yolda daha sonra bu yöntemi belgedeki VBA kodundan çağıracaksınız.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/CallingCodeFromVBA/ThisDocument.vb" id="Snippet1":::

3. Projeyi derleyin.

## <a name="expose-the-method-to-vba-code"></a>Yöntemi VBA koduna sunun
 `CreateTable`BELGEDEKI VBA kodunda yöntemi göstermek için, konak öğesi Için **EnableVbaCallers** özelliğini `ThisDocument` **true** olarak ayarlayın.

### <a name="to-expose-the-method-to-vba-code"></a>Yöntemi VBA koduna göstermek için

1. **Çözüm Gezgini**, **ThisDocument. vb** öğesine çift tıklayın.

     **DocumentWithVBA** dosyası tasarımcıda açılır.

2. **Özellikler** penceresinde, **EnableVbaCallers** özelliğini seçin ve değeri **true** olarak değiştirin.

3. Görüntülenen iletide **Tamam** ' a tıklayın.

4. Projeyi derleyin.

## <a name="call-the-method-from-vba-code"></a>VBA kodundan yöntemi çağırma
 Artık `CreateTable` BELGEDEKI VBA kodundan yöntemi çağırabilirsiniz.

> [!NOTE]
> Bu izlenecek yolda, projede hata ayıklarken VBA kodunu belgeye ekleyeceksiniz. bu belgeye eklediğiniz VBA kodu, projeyi bir sonraki sefer oluşturduğunuzda üzerine yazılır, çünkü Visual Studio yapı çıkış klasöründeki belgeyi ana proje klasöründen belgenin bir kopyasıyla değiştirir. VBA kodunu kaydetmek istiyorsanız proje klasöründeki belgeyi belgeye kopyalayabilirsiniz. Daha fazla bilgi için bkz. [VBA ve belge düzeyi özelleştirmelerini birleştirme](../vsto/combining-vba-and-document-level-customizations.md).

### <a name="to-call-the-method-from-vba-code"></a>VBA kodundan yöntemi çağırmak için

1. Projenizi çalıştırmak için **F5** tuşuna basın.

2. **Geliştirici** sekmesinde, **kod** grubunda **Visual Basic**' a tıklayın.

     Visual Basic düzenleyicisi açılır.

3. **Ekle** menüsünde **Modül**' e tıklayın.

4. Aşağıdaki kodu Yeni modüle ekleyin.

     Bu kod, `CreateTable` özelleştirme derlemesindeki yöntemini çağırır. Makro, nesnesinin özelliğini kullanarak bu yönteme erişir `CallVSTOAssembly` `ThisDocument` . Bu özellik, bu kılavuzda daha önce, **EnableVbaCallers** özelliğini ayarladığınızda otomatik olarak oluşturulmuştur.

    ```vb
    Sub CreateTable()
        Call ThisDocument.CallVSTOAssembly.CreateTable("Employee Name", "Start Date")
    End Sub
    ```

5. **F5** tuşuna basın.

6. Belgeye yeni bir tablo eklendiğini doğrulayın.

7. Değişikliklerinizi kaydetmeden Word 'den çıkın.

## <a name="next-steps"></a>Sonraki adımlar
 bu konularda, VBA 'dan Office çözümlerinde kod çağırma hakkında daha fazla bilgi edinebilirsiniz:

- VBA 'dan bir Visual C# özelleştirmesindeki kodu çağırın. bu işlem Visual Basic işlemden farklıdır. Daha fazla bilgi için bkz. [Izlenecek yol: Visual C&#35; PROJESINDEKI VBA 'dan kod çağırma](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md).

- VBA 'dan bir VSTO eklentisinde kodu çağırın. daha fazla bilgi için bkz. [izlenecek yol: VSTO eklentisinde VBA 'dan kod çağırma](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).

## <a name="see-also"></a>Ayrıca bkz.
- [VBA ve belge düzeyi özelleştirmelerini birleştirme](../vsto/combining-vba-and-document-level-customizations.md)
- [Program belge düzeyi özelleştirmeleri](../vsto/programming-document-level-customizations.md)
- [nasıl yapılır: Visual Basic projesindeki kodu VBA 'de kullanıma sunma](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)
- [Nasıl yapılır: Visual C&#35; projesinde kodu VBA 'de kullanıma sunma](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)
- [İzlenecek yol: Visual C&#35; projesindeki VBA 'dan kod çağırma](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)
