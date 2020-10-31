---
title: Kullanımından oluştur ile test-ilk geliştirme
ms.custom: SEO-VS-2020
ms.date: 10/09/2017
dev_langs:
- VB
- CSharp
ms.topic: how-to
helpviewer_keywords:
- Generate From Usage
- Test-First Development
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 26d12801f4397cbca1e9d4c0334f18908f93aecd
ms.sourcegitcommit: f1bb1b66ed141837e992b3352ce68ff24c11f53e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93102616"
---
# <a name="walkthrough-test-first-development-with-the-generate-from-usage-feature"></a>İzlenecek yol: kullanımdan oluştur özelliğinden önce test geliştirme

Bu konu başlığı altında, test-ilk geliştirmeyi destekleyen [kullanım dışı oluşturma](../ide/visual-csharp-intellisense.md#generate-from-usage) özelliğinin nasıl kullanılacağı gösterilmektedir.

 *Test-ilk geliştirme* , ürün belirtimlerine göre birim testlerini ilk kez yazacağınız ve sonra testlerin başarılı olması için gereken kaynak kodu yazdığınız yazılım tasarımına yönelik bir yaklaşımdır. Visual Studio, tanımlanmadan önce test çalışmalarınıza ilk kez başvurduğunuzda kaynak kodunda yeni türler ve Üyeler oluşturarak test ilk geliştirmeyi destekler.

Visual Studio, iş akışınız için en az kesintiyle yeni türler ve Üyeler oluşturur. Türler, Yöntemler, özellikler, alanlar veya oluşturucular için kod içinde geçerli konumunuzu bırakmadan, saplamalar oluşturabilirsiniz. Tür oluşturma seçeneklerini belirtmek için bir iletişim kutusu açtığınızda, odak iletişim kutusu kapandığında geçerli açık dosyaya hemen döner.

**Kullanımdan oluştur** özelliği, Visual Studio ile tümleştirilen test çerçeveleri ile birlikte kullanılabilir. Bu konuda, Microsoft birim testi çerçevesi gösterilmiştir.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="create-a-windows-class-library-project-and-a-test-project"></a>Windows sınıf kitaplığı projesi ve test projesi oluşturma

1. C# veya Visual Basic 'de yeni bir **Windows sınıf kitaplığı** projesi oluşturun. `GFUDemo_VB` `GFUDemo_CS` Kullandığınız dile bağlı olarak veya olarak adlandırın.

2. **Çözüm Gezgini** , üstteki çözüm simgesine sağ tıklayın, **Add**  >  **Yeni proje** Ekle ' yi seçin.

3. Yeni bir **birim testi projesi (.NET Framework)** projesi oluşturun.

   ::: moniker range="vs-2017"

   Aşağıdaki çizimde, C# şablonları için **Yeni proje** iletişim kutusu gösterilmektedir.

   ![Birim testi proje şablonu](../ide/media/newproject_test.png)

   ::: moniker-end

### <a name="add-a-reference-to-the-class-library-project"></a>Sınıf kitaplığı projesine bir başvuru ekleyin

1. **Çözüm Gezgini** , birim testi projeniz altında, **Başvurular** girişine sağ tıklayın ve **Başvuru Ekle** ' yi seçin.

2. **Başvuru Yöneticisi** iletişim kutusunda, **Projeler** ' i seçin ve ardından Sınıf Kitaplığı projesini seçin.

3. **Tamam ' ı** seçerek **başvuru Yöneticisi** iletişim kutusunu kapatın.

4. Çözümünüzü kaydedin. Artık testleri yazmaya başlamaya hazırsınız.

### <a name="generate-a-new-class-from-a-unit-test"></a>Birim testinizden yeni bir sınıf oluşturma

1. Test projesi *UnitTest1* adlı bir dosya içerir. Kod düzenleyicisinde açmak için **Çözüm Gezgini** bu dosyaya çift tıklayın. Test sınıfı ve test yöntemi üretildi.

2. Sınıfının bildirimini bulun `UnitTest1` ve olarak yeniden adlandırın `AutomobileTest` .

   > [!NOTE]
   > IntelliSense artık IntelliSense deyimin tamamlanması için iki alternatif sağlıyor: *tamamlama modu* ve *öneri modu* . Sınıfların ve üyelerin tanımlanmadan önce kullanıldığı durumlar için öneri modunu kullanın. Bir **IntelliSense** penceresi açıkken, **Ctrl** + **Alt** + tamamlama modu ve öneri modu arasında geçiş yapmak için Ctrl alt **alanına** basabilirsiniz. Daha fazla bilgi için bkz. [IntelliSense 'ı kullanma](../ide/using-intellisense.md) . Öneri modu, bir sonraki adımda yazarken yardımcı olur `Automobile` .

3. Yöntemini bulun `TestMethod1()` ve olarak yeniden adlandırın `DefaultAutomobileIsInitializedCorrectly()` . Bu yöntemin içinde, aşağıdaki ekran görüntülerinde gösterildiği gibi adlı bir sınıfın yeni bir örneğini oluşturun `Automobile` . Bir derleme zamanı hatası gösteren dalgalı alt çizgi görünür ve sol kenar boşluğunda veya üzerine geldiğinizde doğrudan dalgalı bir [eylem](../ide/quick-actions.md) hatası ampulü görünür.

    ![Visual Basic hızlı eylemler](../ide/media/genclass_underlinevb.png)

    ![C&#35; hızlı eylemler](../ide/media/genclass_underline.png)

4. **Hızlı eylemler** Ampul ampul ' i seçin veya tıklayın. Türün tanımlı olmadığını belirten bir hata iletisi görürsünüz `Automobile` . Ayrıca, bazı çözümler de sunulur.

5. **Tür oluştur** iletişim kutusunu açmak için **yeni tür oluştur** ' a tıklayın. Bu iletişim kutusu, türü farklı bir projede oluşturmayı içeren seçenekler sağlar.

6. **Proje** listesinde, Visual Studio 'nun dosyayı test projesi yerine sınıf kitaplığı projesine eklemesini Istemek Için **gfudemo \_ vb** veya **GFUDemo_CS** ' a tıklayın. Henüz seçili değilse, **yeni dosya oluştur** ' u seçin ve *automobile.cs* veya *otomobil. vb* olarak adlandırın.

     ![Yeni tür oluştur iletişim kutusu](../ide/media/genotherdialog.png)

7. İletişim kutusunu kapatmak ve yeni dosyayı oluşturmak için **Tamam** ' ı tıklatın.

8. **Çözüm Gezgini** , yeni *otomobil. vb* veya *automobile.cs* dosyasının orada olduğunu doğrulamak için, **GFUDemo_VB** veya **GFUDemo_CS** proje düğümüne bakın. Kod düzenleyicisinde, odak hala içinde olduğundan `AutomobileTest.DefaultAutomobileIsInitializedCorrectly` , testinizi en az kesintiyle yazmaya devam etmenizi sağlar.

### <a name="generate-a-property-stub"></a>Özellik saplaması oluştur
Ürün belirtiminin, `Automobile` sınıfının ve adında iki ortak özelliğe sahip olduğunu varsayalım `Model` `TopSpeed` . Bu özelliklerin varsayılan ve varsayılan oluşturucularla başlatılması gerekir `"Not specified"` `-1` . Aşağıdaki birim testi varsayılan oluşturucunun özellikleri doğru varsayılan değerlerine ayarladiğini doğrular.

1. Aşağıdaki kod satırını `DefaultAutomobileIsInitializedCorrectly` test yöntemine ekleyin.

     [!code-csharp[VbTDDWalkthrough#1](../ide/codesnippet/CSharp/walkthrough-test-first-support-with-the-generate-from-usage-feature_1.cs)]
     [!code-vb[VbTDDWalkthrough#1](../ide/codesnippet/VisualBasic/walkthrough-test-first-support-with-the-generate-from-usage-feature_1.vb)]

2. Kod, üzerinde iki tanımsız özelliğe başvurduğundan `Automobile` , ve altında dalgalı bir alt çizgi `Model` görünür `TopSpeed` . Üzerine gelin `Model` ve **hızlı eylemler** hatası ampul ' i seçin ve ardından **' otomobil mobil. model ' özelliğini oluştur** ' u seçin.

3. Özelliği için aynı şekilde bir özellik saplaması oluşturun `TopSpeed` .

     `Automobile`Sınıfında, yeni özelliklerin türleri içerikten doğru şekilde algılanır.

### <a name="generate-a-stub-for-a-new-constructor"></a>Yeni Oluşturucu için saplama oluşturma
Şimdi ve özelliklerini başlatmak için bir Oluşturucu saplaması oluşturacak bir test yöntemi oluşturacağız `Model` `TopSpeed` . Daha sonra, testi tamamlamaya daha fazla kod ekleyeceksiniz.

1. Aşağıdaki ek test yöntemini `AutomobileTest` sınıfınıza ekleyin.

     [!code-csharp[VbTDDWalkthrough#2](../ide/codesnippet/CSharp/walkthrough-test-first-support-with-the-generate-from-usage-feature_2.cs)]
     [!code-vb[VbTDDWalkthrough#2](../ide/codesnippet/VisualBasic/walkthrough-test-first-support-with-the-generate-from-usage-feature_2.vb)]

2. Kırmızı dalgalı çizgi altındaki **hızlı eylem** hatası ampulü ve ardından **' otomobil ' içinde Oluşturucu üret** ' e tıklayın.

     `Automobile`Sınıf dosyasında, yeni oluşturucunun Oluşturucu çağrısında kullanılan yerel değişkenlerin adlarını incelediğine, sınıfta aynı adlara sahip olan özelliklerin bulunduğunu `Automobile` ve bağımsız değişken değerlerini ve özelliklerinde depolamak için Oluşturucu gövdesinde sağlanan kodu içerdiğine dikkat edin `Model` `TopSpeed` .

3. Yeni oluşturucuyu oluşturduktan sonra, içindeki varsayılan oluşturucuya yapılan çağrının altında dalgalı bir alt çizgi görünür `DefaultAutomobileIsInitializedCorrectly` . Hata iletisi, `Automobile` sınıfın sıfır bağımsız değişken alan bir Oluşturucusu olmadığını belirtir. Parametreleri olmayan açık bir varsayılan oluşturucu oluşturmak için **hızlı eylemler** hata ışığı ampul ' e tıklayın ve ardından **' otomobil ' içinde Oluşturucu oluştur** ' a tıklayın.

### <a name="generate-a-stub-for-a-method"></a>Bir yöntem için saplama oluşturma
Belirtiminin, `Automobile` `IsRunning` `Model` ve `TopSpeed` özellikleri varsayılan değerlerden başka bir şeye ayarlandıysa, bir duruma yeni bir durum koyabileceğini belirtir.

1. Yöntemine aşağıdaki satırları ekleyin `AutomobileWithModelNameCanStart` .

     [!code-csharp[VbTDDWalkthrough#3](../ide/codesnippet/CSharp/walkthrough-test-first-support-with-the-generate-from-usage-feature_3.cs)]
     [!code-vb[VbTDDWalkthrough#3](../ide/codesnippet/VisualBasic/walkthrough-test-first-support-with-the-generate-from-usage-feature_3.vb)]

2. Yöntem çağrısı için **hızlı eylemler** hata ışığı ampul ' i tıklatın `myAuto.Start` ve ardından **' otomobil. Başlat ' metodunu üret** ' e tıklayın.

3. Özelliği için **hızlı eylemler** ampul ' i `IsRunning` ve sonra **' otomobil. IsRunning ' özelliğini oluştur** ' a tıklayın.

     `Automobile`Sınıfı artık adlı bir yöntemi `Start()` ve adında bir özelliği içerir `IsRunning` .

### <a name="run-the-tests"></a>Testleri çalıştırma

1. **Test** menüsünde **Run**  >  **tüm testleri** Çalıştır ' ı seçin.

     **Run**  >  **Tüm testleri** Çalıştır komutu, geçerli çözüm için yazılmış tüm test çerçevelerinden tüm testleri çalıştırır. Bu durumda, iki test vardır ve beklendiği gibi her ikisi de başarısız olur. `DefaultAutomobileIsInitializedCorrectly`Koşul döndürdüğü için test başarısız olur `Assert.IsTrue` `False` . `AutomobileWithModelNameCanStart` `Start` `Automobile` Sınıftaki yöntem bir özel durum oluşturduğundan test başarısız olur.

     **Test sonuçları** penceresi aşağıdaki çizimde gösterilmiştir.

     ![Başarısız olan test sonuçları](../ide/media/testsfailed.png)

2. **Test sonuçları** penceresinde her bir testin konumuna gitmek için her bir test sonucu satırına çift tıklayın.

### <a name="implement-the-source-code"></a>Kaynak kodunu uygulama

1. , `Model` `TopSpeed` Ve `IsRunning` özelliklerinin tamamı,, ve `"Not specified"` `-1` `False` (veya `false` C# için) doğru varsayılan değerlerine başlatıldığından, varsayılan oluşturucuya aşağıdaki kodu ekleyin.

     [!code-csharp[VbTDDWalkthrough#5](../ide/codesnippet/CSharp/walkthrough-test-first-support-with-the-generate-from-usage-feature_5.cs)]
     [!code-vb[VbTDDWalkthrough#5](../ide/codesnippet/VisualBasic/walkthrough-test-first-support-with-the-generate-from-usage-feature_5.vb)]

2. `Start`Yöntemi çağrıldığında, `IsRunning` bayrağı true olarak ayarlamanız gerekir, `Model` Aksi takdirde veya `TopSpeed` özellikleri varsayılan değerleri dışında bir değere ayarlanır. `NotImplementedException`Yöntemini Yöntem gövdesinden kaldırın ve aşağıdaki kodu ekleyin.

     [!code-csharp[VbTDDWalkthrough#6](../ide/codesnippet/CSharp/walkthrough-test-first-support-with-the-generate-from-usage-feature_6.cs)]
     [!code-vb[VbTDDWalkthrough#6](../ide/codesnippet/VisualBasic/walkthrough-test-first-support-with-the-generate-from-usage-feature_6.vb)]

### <a name="run-the-tests-again"></a>Testleri yeniden çalıştırın

- **Test** menüsünde, **Çalıştır** ' ın üzerine gelin ve ardından **tüm sınamalar** ' ı tıklatın.

     Testlerin geçişi bu kez yapılır. **Test sonuçları** penceresi aşağıdaki çizimde gösterilmiştir.

     ![Geçilen test sonuçları](../ide/media/testspassed.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Kullanımdan oluştur](../ide/visual-csharp-intellisense.md#generate-from-usage)
- [Kod düzenleyicisinin özellikleri](../ide/writing-code-in-the-code-and-text-editor.md)
- [IntelliSense kullanma](../ide/using-intellisense.md)
- [Kodunuzun birim testi](../test/unit-test-your-code.md)
- [Hızlı Eylemler](../ide/quick-actions.md)
