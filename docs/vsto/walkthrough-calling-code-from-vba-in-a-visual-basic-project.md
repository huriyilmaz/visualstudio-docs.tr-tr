---
title: "Adım adım kılavuz: Visual Basic projesinde VBA'dan kod çağırma"
description: Belge düzeyi özelleştirmesinde, belge Microsoft Word (VBA) Visual Basic for Applications yöntemini çağırmayı öğrenin.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122147654"
---
# <a name="walkthrough-call-code-from-vba-in-a-visual-basic-project"></a>Adım adım kılavuz: Visual Basic projesinde VBA'dan kod çağırma
  Bu kılavuzda, belge içinde Visual Basic for Applications (VBA) kodundan Microsoft Office Word için belge düzeyi özelleştirmede bir yöntemin nasıl çağrılacağını gösterir. Yordam üç temel adımdan oluşur: konak öğesi sınıfına bir yöntem ekleyin, yöntemi VBA koduna açın ve ardından belgede VBA kodundan `ThisDocument` yöntemini çağırma.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Bu kılavuz özellikle Word kullanıyor olsa da, izlenecek yol tarafından gösterilen kavramlar, belge düzeyi projeleri için de Excel.

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- VBA kodu içeren bir belge oluşturma.

- Word'de Güven Merkezi'ne kullanarak belgenin bulunduğu konuma güvenme.

- Konak öğe sınıfına `ThisDocument` bir yöntem ekleme.

- Yöntemi VBA koduna ifşa etmek.

- VBA kodundan yöntemini çağırma.

> [!NOTE]
> Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için [bkz. IDE'Visual Studio kişiselleştirme.](../ide/personalizing-the-visual-studio-ide.md)

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word

## <a name="create-a-document-that-contains-vba-code"></a>VBA kodu içeren bir belge oluşturma
 İlk adım, basit bir VBA makrosu içeren makro özellikli bir belge oluşturmaktır. Belge, bu belgeyi temel alan bir Visual Studio vbA projesi içermesi gerekir. Aksi Visual Studio vbA kodunu özelleştirme derlemesine çağırabilecek şekilde VBA projesini değiştiremezsiniz.

 Kullanmak istediğiniz VBA kodunu içeren bir belgeniz zaten varsa bu adımı atlayabilirsiniz.

### <a name="to-create-a-document-that-contains-vba-code"></a>VBA kodu içeren bir belge oluşturmak için

1. Word'i başlat.

2. Etkin belgeyi **DocumentWithVBA** adıyla Word Makro Özellikli Belge **( \* .docm)** olarak kaydedin. Masaüstü gibi uygun bir konuma kaydedin.

3. Şeritte Geliştirici **sekmesine** tıklayın.

    > [!NOTE]
    > Geliştirici **sekmesi** görünmüyorsa, önce bunu göstermeniz gerekir. Daha fazla bilgi için [şeritteki Geliştirici sekmesini gösterme.](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)

4. Kod **grubunda,** **Visual Basic.**

     Visual Basic Düzenleyicisi açılır.

5. Bu **Project** **ThisDocument'a çift tıklayın.**

     Nesnenin kod `ThisDocument` dosyası açılır.

6. Aşağıdaki VBA kodunu kod dosyasına ekleyin. Bu kod, hiçbir şey yapacak basit bir işlev tanımlar. Bu işlevin tek amacı belgede bir VBA projesinin mevcut olduğundan emin olmaktır. Bu, bu kılavuzda yer alan sonraki adımlar için gereklidir.

    ```vb
    Sub EmptySub()
    End Sub
    ```

7. Belgeyi kaydedin ve Word'den çıkın.

## <a name="create-the-project"></a>Proje oluşturma
 Şimdi Word için daha önce oluşturduğunuz makro özellikli belgeyi kullanan bir belge düzeyi projesi oluşturabilirsiniz.

### <a name="to-create-a-new-project"></a>Yeni proje oluşturmak için

1. 'i [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] başlatma.

2. Dosya menüsünde **Yeni'nin** üzerine **gelin ve** ardından Dosya'ya **Project.** IDE'niz geliştirme ayarlarını Visual Basic olarak ayarlanmışsa  Dosya menüsünde Yeni Uygulama'ya **Project.**

3. Şablonlar bölmesinde, **Visual Basic'Office/SharePoint.** 

4. Office **düğümünü** seçin.

5. Proje şablonları listesinde Word **2010** Belgesi veya **Word 2013 Belge projesini** seçin.

6. Ad **kutusuna** **CallingCodeFromVBA yazın.**

7. **Tamam**'a tıklayın.

     Office için Visual Studio Araçları Project **Sihirbazı** açılır.

8. Var **olan bir belgeyi** kopyala'yı seçin ve var olan belge kutusunun Tam yolu'nda, daha önce oluşturduğunuz **DocumentWithVBA** belgesinin konumunu belirtin.  Makro özellikli kendi belgenizi kullanıyorsanız, bunun yerine bu belgenin konumunu belirtin.

9. **Finish (Son)** düğmesine tıklayın.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**DocumentWithVBA belgesini** tasarımcıda açar ve **CallingCodeFromVBA projesini** **Çözüm Gezgini.**

## <a name="trust-the-location-of-the-document"></a>Belgenin bulunduğu konuma güvenin
 Çözüm belgesinde VBA kodunun kodunun açığa çıkarılamadan önce, çalıştıracak belgede VBA'ya güvenmeniz gerekir. Bunu yapmanın birkaç yolu vardır. Bu kılavuz için Word'de Güven Merkezi'nde belgenin **bulunduğu konuma** güvenin.

### <a name="to-trust-the-location-of-the-document"></a>Belgenin bulunduğu konuma güvenmek için

1. Word'i başlat.

2. Dosya **sekmesine** tıklayın.

3. Sözcük Seçenekleri **düğmesine** tıklayın.

4. Kategoriler bölmesinde Güven **Merkezi'ne tıklayın.**

5. Ayrıntılar bölmesinde Güven Merkezi'ne **tıklayın ve Ayarlar.**

6. Kategoriler bölmesinde Güvenilen **Konumlar'a tıklayın.**

7. Ayrıntılar bölmesinde Yeni konum **ekle'ye tıklayın.**

8. Güvenilen **Microsoft Office iletişim kutusunda,** **CallingCodeFromVBA** projesini içeren klasöre göz atabilirsiniz.

9. Bu **konumun alt klasörlerine de güvenilir'i seçin.**

10. Güvenilen Microsoft Office **iletişim kutusunda** Tamam'a **tıklayın.**

11. Güven Merkezi **iletişim kutusunda** Tamam'a **tıklayın.**

12. Sözcük Seçenekleri **iletişim kutusunda** Tamam'a **tıklayın.**

13. Word'den çıkın.

## <a name="add-a-method-to-the-thisdocument-class"></a>ThisDocument sınıfına yöntem ekleme
 VBA projesi ayarnana göre, VBA kodundan çağırabilirsiniz `ThisDocument` konak öğesi sınıfına bir yöntem ekleyin.

### <a name="to-add-a-method-to-the-thisdocument-class"></a>ThisDocument sınıfına bir yöntem eklemek için

1. Bu **Çözüm Gezgini** **ThisDocument.vb'ye sağ tıklayın** ve ardından Kodu **Görüntüle'ye tıklayın.**

     **ThisDocument.vb** dosyası Kod Düzenleyicisi'nde açılır.

2. Sınıfına aşağıdaki yöntemi `ThisDocument` ekleyin. Bu yöntem, belgenin başında iki satır ve iki sütun içeren bir tablo oluşturur. Parametreler, ilk satırda görüntülenen metni belirtir. Bu kılavuzda daha sonra, belgede VBA kodundan bu yöntemi çağıracağız.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/CallingCodeFromVBA/ThisDocument.vb" id="Snippet1":::

3. Projeyi derleyin.

## <a name="expose-the-method-to-vba-code"></a>VbA kodunun yöntemini ortaya çıkarma
 Belgede `CreateTable` vbA kodunda yöntemini açığa çıkarmak için konak öğesi **için EnableVbaCallers** `ThisDocument` özelliğini True olarak **ayarlayın.**

### <a name="to-expose-the-method-to-vba-code"></a>Yöntemi VBA koduna göstermek için

1. içinde **Çözüm Gezgini** **ThisDocument.vb'ye çift tıklayın.**

     **DocumentWithVBA** dosyası tasarımcıda açılır.

2. Özellikler **penceresinde** **EnableVbaCallers özelliğini** seçin ve değeri True olarak **değiştirin.**

3. Görüntülenen **iletide** Tamam'a tıklayın.

4. Projeyi derleyin.

## <a name="call-the-method-from-vba-code"></a>VBA kodundan yöntemini çağırma
 Artık belgede `CreateTable` VBA kodundan yöntemini çağırabilirsiniz.

> [!NOTE]
> Bu kılavuzda, projede hata ayıklarken belgeye VBA kodu eksersiniz. Visual Studio, derleme çıktı klasöründeki belgeyi ana proje klasöründeki belgenin bir kopyasıyla değiştireceğini için, projeyi bir sonraki derlemesinde bu belgeye ekley istediğiniz VBA kodunun üzerine yazılır. VBA kodunu kaydetmek için proje klasöründeki belgeye kopyaabilirsiniz. Daha fazla bilgi için [bkz. VBA ve belge düzeyinde özelleştirmeleri birleştirme.](../vsto/combining-vba-and-document-level-customizations.md)

### <a name="to-call-the-method-from-vba-code"></a>VBA kodundan yöntemini çağırma

1. Projenizi **çalıştırmak için F5** tuşuna basın.

2. Geliştirici **sekmesinde,** Kod **grubunda,** Kod'a **Visual Basic.**

     Visual Basic Düzenleyicisi açılır.

3. Ekle menüsünde **Modül'e** **tıklayın.**

4. Aşağıdaki kodu yeni modüle ekleyin.

     Bu kod, özelleştirme `CreateTable` derlemesinde yöntemini arar. Makro, nesnesinin özelliğini kullanarak `CallVSTOAssembly` bu yönteme `ThisDocument` erişer. Bu özellik, bu kılavuzda daha önce **EnableVbaCallers** özelliğini ayar her zaman otomatik olarak oluşturulur.

    ```vb
    Sub CreateTable()
        Call ThisDocument.CallVSTOAssembly.CreateTable("Employee Name", "Start Date")
    End Sub
    ```

5. **F5 tuşuna basın.**

6. Belgeye yeni bir tablo ekli olduğunu doğrulayın.

7. Değişikliklerinizi kaydetmeden Word'den çıkın.

## <a name="next-steps"></a>Sonraki adımlar
 VbA'dan kod çağırma hakkında daha fazla Office şu konulardan öğrenebilirsiniz:

- VBA'dan Visual C# özelleştirmesinde kod çağırma. Bu işlem, işlemden Visual Basic farklıdır. Daha fazla bilgi için [bkz. Walkthrough: Visual C&#35; projesinde VBA'dan kod çağırma.](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)

- VBA'dan VSTO eklentisinde kod çağırma. Daha fazla bilgi için bkz. Adım [adım: VBA'dan VSTO kod çağırma.](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)

## <a name="see-also"></a>Ayrıca bkz.
- [VBA ve belge düzeyi özelleştirmelerini birleştirme](../vsto/combining-vba-and-document-level-customizations.md)
- [Program belge düzeyi özelleştirmeleri](../vsto/programming-document-level-customizations.md)
- [Nasıl olur: Visual Basic projesinde kodu VBA'Visual Basic açığa çıkarma](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)
- [Nasıl olur: Visual C çalışma grubu projesinde kodu VBA'&#35; açığa çıkarma](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)
- [Adım adım kılavuz: Visual C çalışma grubu projesinde VBA'dan&#35; çağırma](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)
