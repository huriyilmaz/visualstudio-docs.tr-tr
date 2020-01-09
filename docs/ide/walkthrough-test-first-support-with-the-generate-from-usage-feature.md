---
title: Kullanım özelliğinden Oluştur özelliği ile test-ilk geliştirme
ms.date: 10/09/2017
dev_langs:
- VB
- CSharp
ms.topic: conceptual
helpviewer_keywords:
- Generate From Usage
- Test-First Development
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9bf9a7e613a482167a01739320282f9ba8fdea26
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596898"
---
# <a name="walkthrough-test-first-development-with-the-generate-from-usage-feature"></a>İzlenecek yol: kullanımdan oluştur özelliğinden önce test geliştirme

Bu konu başlığı altında, test-ilk geliştirmeyi destekleyen [kullanım dışı oluşturma](../ide/visual-csharp-intellisense.md#generate-from-usage) özelliğinin nasıl kullanılacağı gösterilmektedir.

 *Test-ilk geliştirme* , ürün belirtimlerine göre birim testlerini ilk kez yazacağınız ve sonra testlerin başarılı olması için gereken kaynak kodu yazdığınız yazılım tasarımına yönelik bir yaklaşımdır. Visual Studio, tanımlanmadan önce test çalışmalarınıza ilk kez başvurduğunuzda kaynak kodunda yeni türler ve Üyeler oluşturarak test ilk geliştirmeyi destekler.

Visual Studio, iş akışınız için en az kesintiyle yeni türler ve Üyeler oluşturur. Türler, Yöntemler, özellikler, alanlar veya oluşturucular için kod içinde geçerli konumunuzu bırakmadan, saplamalar oluşturabilirsiniz. Tür oluşturma seçeneklerini belirtmek için bir iletişim kutusu açtığınızda, odak iletişim kutusu kapandığında geçerli açık dosyaya hemen döner.

**Kullanımdan oluştur** özelliği, Visual Studio ile tümleştirilen test çerçeveleri ile birlikte kullanılabilir. Bu konuda, Microsoft birim testi çerçevesi gösterilmiştir.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="create-a-windows-class-library-project-and-a-test-project"></a>Windows sınıf kitaplığı projesi ve test projesi oluşturma

1. C# Veya Visual Basic, yeni bir **Windows sınıf kitaplığı** projesi oluşturun. Kullanmakta olduğunuz dile bağlı olarak, `GFUDemo_VB` veya `GFUDemo_CS`adlandırın.

2. **Çözüm Gezgini**, üstteki çözüm simgesine sağ tıklayın, > **Yeni proje** **Ekle** ' yi seçin.

3. Yeni bir **birim testi projesi (.NET Framework)** projesi oluşturun.

   ::: moniker range="vs-2017"

   Aşağıdaki çizimde, şablonlar C# Için **Yeni proje** iletişim kutusu gösterilmektedir.

   ![Birim testi proje şablonu](../ide/media/newproject_test.png)

   ::: moniker-end

### <a name="add-a-reference-to-the-class-library-project"></a>Sınıf kitaplığı projesine bir başvuru ekleyin

1. **Çözüm Gezgini**, birim testi projeniz altında, **Başvurular** girişine sağ tıklayın ve **Başvuru Ekle**' yi seçin.

2. **Başvuru Yöneticisi** iletişim kutusunda, **Projeler** ' i seçin ve ardından Sınıf Kitaplığı projesini seçin.

3. **Tamam ' ı** seçerek **başvuru Yöneticisi** iletişim kutusunu kapatın.

4. Çözümünüzü kaydedin. Artık testleri yazmaya başlamaya hazırsınız.

### <a name="generate-a-new-class-from-a-unit-test"></a>Birim testinizden yeni bir sınıf oluşturma

1. Test projesi *UnitTest1*adlı bir dosya içerir. Kod düzenleyicisinde açmak için **Çözüm Gezgini** bu dosyaya çift tıklayın. Test sınıfı ve test yöntemi üretildi.

2. Sınıf `UnitTest1` bildirimini bulun ve `AutomobileTest`olarak yeniden adlandırın.

   > [!NOTE]
   > IntelliSense artık IntelliSense deyimin tamamlanması için iki alternatif sağlıyor: *tamamlama modu* ve *öneri modu*. Sınıfların ve üyelerin tanımlanmadan önce kullanıldığı durumlar için öneri modunu kullanın. Bir **IntelliSense** penceresi açıkken, tamamlama modu ve öneri modu arasında geçiş yapmak için **Ctrl**+**alt**+**alanına** basabilirsiniz. Daha fazla bilgi için bkz. [IntelliSense 'ı kullanma](../ide/using-intellisense.md) . Öneri modu, bir sonraki adımda `Automobile` yazarken yardımcı olur.

3. `TestMethod1()` yöntemini bulun ve `DefaultAutomobileIsInitializedCorrectly()`olarak yeniden adlandırın. Bu yöntemin içinde, aşağıdaki ekran görüntülerinde gösterildiği gibi, `Automobile`adlı bir sınıfın yeni bir örneğini oluşturun. Bir derleme zamanı hatası gösteren dalgalı alt çizgi görünür ve sol kenar boşluğunda veya üzerine geldiğinizde doğrudan dalgalı bir [eylem](../ide/quick-actions.md) hatası ampulü görünür.

    ![Visual Basic hızlı eylemler](../ide/media/genclass_underlinevb.png)

    ![C 'de hızlı eylemler&#35;](../ide/media/genclass_underline.png)

4. **Hızlı eylemler** Ampul ampul ' i seçin veya tıklayın. `Automobile` türün tanımlanmadığı olduğunu belirten bir hata iletisi görürsünüz. Ayrıca, bazı çözümler de sunulur.

5. **Tür oluştur** iletişim kutusunu açmak için **yeni tür oluştur** ' a tıklayın. Bu iletişim kutusu, türü farklı bir projede oluşturmayı içeren seçenekler sağlar.

6. **Proje** listesinde, Visual Studio 'nun dosyayı test projesi yerine sınıf kitaplığı projesine eklemesini Istemek Için **gfudemo\_vb** veya **GFUDemo_CS** ' e tıklayın. Henüz seçili değilse, **yeni dosya oluştur** ' u seçin ve *automobile.cs* veya *otomobil. vb*olarak adlandırın.

     ![Yeni tür oluştur iletişim kutusu](../ide/media/genotherdialog.png)

7. İletişim kutusunu kapatmak ve yeni dosyayı oluşturmak için **Tamam** ' ı tıklatın.

8. **Çözüm Gezgini**, yeni *otomobil. vb* veya *automobile.cs* dosyasının orada olduğunu doğrulamak için, **GFUDemo_VB** veya **GFUDemo_CS** proje düğümüne bakın. Kod Düzenleyicisi 'nde odak hala `AutomobileTest.DefaultAutomobileIsInitializedCorrectly`, bu da testinizi en az kesintiyle yazmaya devam etmenizi sağlar.

### <a name="generate-a-property-stub"></a>Özellik saplaması oluştur
Ürün belirtiminin `Automobile` sınıfının `Model` ve `TopSpeed`adında iki ortak özelliğe sahip olduğunu varsayalım. Bu özellikler varsayılan Oluşturucu tarafından `"Not specified"` ve `-1` varsayılan değerleriyle başlatılmalıdır. Aşağıdaki birim testi varsayılan oluşturucunun özellikleri doğru varsayılan değerlerine ayarladiğini doğrular.

1. Aşağıdaki kod satırını `DefaultAutomobileIsInitializedCorrectly` test yöntemine ekleyin.

     [!code-csharp[VbTDDWalkthrough#1](../ide/codesnippet/CSharp/walkthrough-test-first-support-with-the-generate-from-usage-feature_1.cs)]
     [!code-vb[VbTDDWalkthrough#1](../ide/codesnippet/VisualBasic/walkthrough-test-first-support-with-the-generate-from-usage-feature_1.vb)]

2. Kod `Automobile`üzerinde iki tanımsız özelliğe başvurduğundan, `Model` ve `TopSpeed`altında dalgalı bir alt çizgi görünür. `Model` üzerine gelin ve **hızlı eylemler** hatası ampul ' i seçin, sonra **' otomobil. model ' özelliğini oluştur**' u seçin.

3. `TopSpeed` özelliği için aynı şekilde bir özellik saplaması oluşturun.

     `Automobile` sınıfında, yeni özelliklerin türleri içerikten doğru şekilde algılanır.

### <a name="generate-a-stub-for-a-new-constructor"></a>Yeni Oluşturucu için saplama oluşturma
Artık `Model` ve `TopSpeed` özelliklerini başlatmak için bir Oluşturucu saplaması oluşturacak bir test yöntemi oluşturacağız. Daha sonra, testi tamamlamaya daha fazla kod ekleyeceksiniz.

1. Aşağıdaki ek test yöntemini `AutomobileTest` sınıfınıza ekleyin.

     [!code-csharp[VbTDDWalkthrough#2](../ide/codesnippet/CSharp/walkthrough-test-first-support-with-the-generate-from-usage-feature_2.cs)]
     [!code-vb[VbTDDWalkthrough#2](../ide/codesnippet/VisualBasic/walkthrough-test-first-support-with-the-generate-from-usage-feature_2.vb)]

2. Kırmızı dalgalı çizgi altındaki **hızlı eylem** hatası ampulü ve ardından **' otomobil ' içinde Oluşturucu üret**' e tıklayın.

     `Automobile` sınıf dosyasında, yeni oluşturucunun Oluşturucu çağrısında kullanılan yerel değişkenlerin adlarını incelediğine, `Automobile` sınıfında aynı adlara sahip olan özelliklerin ve `Model` ve `TopSpeed` özelliklerinde bağımsız değişken değerlerini depolamak için Oluşturucu gövdesinde sağlanan kodun bulunduğunu unutmayın.

3. Yeni oluşturucuyu oluşturduktan sonra, `DefaultAutomobileIsInitializedCorrectly`varsayılan oluşturucuya yapılan çağrının altında dalgalı bir alt çizgi görünür. Hata mesajı, `Automobile` sınıfının sıfır bağımsız değişken alan bir Oluşturucusu olmadığını belirtir. Parametreleri olmayan açık bir varsayılan oluşturucu oluşturmak için **hızlı eylemler** hata ışığı ampul ' e tıklayın ve ardından **' otomobil ' içinde Oluşturucu oluştur**' a tıklayın.

### <a name="generate-a-stub-for-a-method"></a>Bir yöntem için saplama oluşturma
Belirtiminin, `Model` ve `TopSpeed` özellikleri varsayılan değerlerden başka bir değere ayarlandıysa, yeni bir `Automobile` `IsRunning` durumuna koyabileceğini belirtir.

1. `AutomobileWithModelNameCanStart` yöntemine aşağıdaki satırları ekleyin.

     [!code-csharp[VbTDDWalkthrough#3](../ide/codesnippet/CSharp/walkthrough-test-first-support-with-the-generate-from-usage-feature_3.cs)]
     [!code-vb[VbTDDWalkthrough#3](../ide/codesnippet/VisualBasic/walkthrough-test-first-support-with-the-generate-from-usage-feature_3.vb)]

2. `myAuto.Start` yöntemi çağrısı için **hızlı eylemler** hatası ampul ' i tıklatın ve ardından **' otomobil. Başlat ' metodunu üret**' e tıklayın.

3. `IsRunning` özelliği için **hızlı eylemler** ampul ' i ve sonra **' otomobil. IsRunning ' özelliğini oluştur**' a tıklayın.

     `Automobile` sınıfı artık `Start()` adlı bir yöntemi ve `IsRunning`adlı bir özelliği içerir.

### <a name="run-the-tests"></a>Testleri çalıştırın

1. **Test** menüsünde, **Tüm testler** > **Çalıştır** ' ı seçin.

      > **tüm testleri** **Çalıştır** komutu, geçerli çözüm için yazılmış tüm test çerçevelerinden tüm testleri çalıştırır. Bu durumda, iki test vardır ve beklendiği gibi her ikisi de başarısız olur. `Assert.IsTrue` koşulu `False`döndürdüğünden `DefaultAutomobileIsInitializedCorrectly` test başarısız olur. `Automobile` sınıfındaki `Start` yöntemi bir özel durum oluşturduğundan `AutomobileWithModelNameCanStart` test başarısız olur.

     **Test sonuçları** penceresi aşağıdaki çizimde gösterilmiştir.

     ![Başarısız olan test sonuçları](../ide/media/testsfailed.png)

2. **Test sonuçları** penceresinde her bir testin konumuna gitmek için her bir test sonucu satırına çift tıklayın.

### <a name="implement-the-source-code"></a>Kaynak kodunu uygulama

1. `Model`, `TopSpeed` ve `IsRunning` özelliklerinin tümünün `"Not specified"`, `-1`ve `False` doğru varsayılan değerlerine (veya `false` C#) başlatılması için aşağıdaki kodu varsayılan oluşturucuya ekleyin.

     [!code-csharp[VbTDDWalkthrough#5](../ide/codesnippet/CSharp/walkthrough-test-first-support-with-the-generate-from-usage-feature_5.cs)]
     [!code-vb[VbTDDWalkthrough#5](../ide/codesnippet/VisualBasic/walkthrough-test-first-support-with-the-generate-from-usage-feature_5.vb)]

2. `Start` yöntemi çağrıldığında, `IsRunning` bayrağını yalnızca, `Model` veya `TopSpeed` özellikleri varsayılan değerleri dışında bir değere ayarlandıysa true olarak ayarlanmalıdır. Yöntem gövdesinden `NotImplementedException` kaldırın ve aşağıdaki kodu ekleyin.

     [!code-csharp[VbTDDWalkthrough#6](../ide/codesnippet/CSharp/walkthrough-test-first-support-with-the-generate-from-usage-feature_6.cs)]
     [!code-vb[VbTDDWalkthrough#6](../ide/codesnippet/VisualBasic/walkthrough-test-first-support-with-the-generate-from-usage-feature_6.vb)]

### <a name="run-the-tests-again"></a>Testleri yeniden çalıştırın

- **Test** menüsünde, **Çalıştır**' ın üzerine gelin ve ardından **tüm sınamalar**' ı tıklatın.

     Testlerin geçişi bu kez yapılır. **Test sonuçları** penceresi aşağıdaki çizimde gösterilmiştir.

     ![Geçilen test sonuçları](../ide/media/testspassed.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Kullanımdan oluştur](../ide/visual-csharp-intellisense.md#generate-from-usage)
- [Kod Düzenleyicisi özellikleri](../ide/writing-code-in-the-code-and-text-editor.md)
- [IntelliSense kullanma](../ide/using-intellisense.md)
- [Birim testi kod](../test/unit-test-your-code.md)
- [Hızlı Eylemler](../ide/quick-actions.md)
