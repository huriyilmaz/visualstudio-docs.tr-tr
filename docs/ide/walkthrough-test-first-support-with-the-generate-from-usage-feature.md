---
title: Kullanımdan Oluştur özelliği ile test-ilk geliştirme
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596898"
---
# <a name="walkthrough-test-first-development-with-the-generate-from-usage-feature"></a>Walkthrough: Kullanımdan Oluştur özelliğiyle test-ilk geliştirme

Bu konu, ilk test geliştirmeyi destekleyen [Kullanımdan Oluştur](../ide/visual-csharp-intellisense.md#generate-from-usage) özelliğinin nasıl kullanılacağını gösterir.

 *Test-ilk geliştirme,* önce ürün özelliklerine göre birim testleri yazdığınız ve ardından testlerin başarılı olması için gereken kaynak kodunu yazdığınız yazılım tasarımına yönelik bir yaklaşımdır. Visual Studio, tanımlanmadan önce test çalışmalarınızda ilk başvuruyaptığınızda kaynak kodunda yeni türler ve üyeler oluşturarak test ilk geliştirmeyi destekler.

Visual Studio, iş akışınızı en az kesintiye ile yeni türleri ve üyeleri oluşturur. Geçerli konumunuzu kodda bırakmadan türleri, yöntemleri, özellikleri, alanları veya oluşturucular için saplamalar oluşturabilirsiniz. Tür oluşturma seçenekleri belirtmek için bir iletişim kutusu açtığınızda, iletişim kutusu kapandığında odak hemen geçerli açık dosyaya döner.

**Kullanımdan Oluştur** özelliği Visual Studio ile tümlalanan test çerçeveleri ile kullanılabilir. Bu konuda, Microsoft Birimi Sınama Çerçevesi gösterilmiştir.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="create-a-windows-class-library-project-and-a-test-project"></a>Windows Sınıf Kitaplığı projesi ve Test projesi oluşturma

1. C# veya Visual Basic'te yeni bir **Windows Sınıf Kitaplığı** projesi oluşturun. Kullandığınız `GFUDemo_VB` dile `GFUDemo_CS`bağlı olarak adlandırın veya.

2. **Çözüm Gezgini'nde,** üstteki çözüm simgesine sağ tıklayın,**Yeni Proje** **Ekle'yi** > seçin.

3. Yeni bir **Birim Test Projesi (.NET Framework)** projesi oluşturun.

   ::: moniker range="vs-2017"

   Aşağıdaki resimde C# şablonları için **Yeni Proje** iletişim kutusu gösterilmektedir.

   ![Ünite Test Projesi şablonu](../ide/media/newproject_test.png)

   ::: moniker-end

### <a name="add-a-reference-to-the-class-library-project"></a>Sınıf Kitaplığı projesine başvuru ekleme

1. **Çözüm Gezgini'nde,** birim test projeniz in altında, **Referanslar** girişine sağ tıklayın ve **Referans Ekle'yi**seçin.

2. Başvuru **Yöneticisi** iletişim kutusunda **Projeler'i** seçin ve ardından sınıf kitaplığı projesini seçin.

3. **Başvuru Yöneticisi** iletişim kutusunu kapatmak için **Tamam'ı** seçin.

4. Çözümünüzü kaydedin. Artık testler yazmaya başlamaya hazırsınız.

### <a name="generate-a-new-class-from-a-unit-test"></a>Birim testinden yeni bir sınıf oluşturma

1. Test projesi *UnitTest1*adlı bir dosya içerir. Kod düzenleyicisinde açmak için **Solution Explorer'da** bu dosyayı çift tıklatın. Bir test sınıfı ve test yöntemi oluşturuldu.

2. Sınıf `UnitTest1` için bildirgeyi bulun `AutomobileTest`ve yeniden adlandırın.

   > [!NOTE]
   > IntelliSense şimdi IntelliSense deyimi nin tamamlanması için iki alternatif sunar: *tamamlama modu* ve *öneri modu.* Sınıfların ve üyelerin tanımlanmadan önce kullanıldığı durumlar için öneri modunu kullanın. Bir **IntelliSense** penceresi açıldığında, tamamlama modu ve öneri modu arasında geçiş yapmak için **Ctrl**+**Alt**+**Space** tuşuna basabilirsiniz. Daha fazla bilgi için [IntelliSense'i kullanın.](../ide/using-intellisense.md) Öneri modu, bir sonraki `Automobile` adımı yazarken yardımcı olacaktır.

3. `TestMethod1()` Yöntemi bulun ve `DefaultAutomobileIsInitializedCorrectly()`yeniden adlandırın. Bu yöntemin içinde, aşağıdaki ekran `Automobile`görüntülerinde gösterildiği gibi, adlı sınıfın yeni bir örneğini oluşturun. Dalgalı bir alt çizgi, bir derleme zamanı hatası gösterir ve [bir Hızlı Eylemler](../ide/quick-actions.md) hata ampul sol kenar boşluğunda görünür, ya da doğrudan üzerinde gezinirseniz kıvrım altında.

    ![Visual Basic'te Hızlı İşlemler](../ide/media/genclass_underlinevb.png)

    ![C&#35; Hızlı Eylemler](../ide/media/genclass_underline.png)

4. **Hızlı Eylemler** ampulü seçin veya tıklatın. Türün `Automobile` tanımlanmadığını belirten bir hata iletisi görürsünüz. Ayrıca bazı çözümler ile sunulmaktadır.

5. **Türü Oluştur** iletişim kutusunu açmak için **yeni tür** oluştur'u tıklatın. Bu iletişim kutusu, farklı bir projede tür oluşturmayı içeren seçenekler sağlar.

6. **Proje** listesinde, Visual Studio'ya dosyayı test projesi yerine sınıf kitaplığı projesine eklemesi için talimat vermek için **GFUDemo\_VB** veya **GFUDemo_CS'yi** tıklatın. Zaten seçilmemişse, **yeni dosya oluştur'u** seçin ve *dosyayı Automobile.cs* veya *Automobile.vb*olarak adlandırın.

     ![Yeni Tür iletişim kutusu oluşturma](../ide/media/genotherdialog.png)

7. İletişim kutusunu kapatmak ve yeni dosyayı oluşturmak için **Tamam'ı** tıklatın.

8. **Çözüm Gezgini'nde,** yeni *Automobile.vb* veya *Automobile.cs* dosyasının orada olduğunu doğrulamak için **GFUDemo_VB** veya **GFUDemo_CS** proje düğümünün altına bakın. Kod düzenleyicisinde, odak hala `AutomobileTest.DefaultAutomobileIsInitializedCorrectly`, hangi kesinti en az test yazmaya devam etmenizi sağlar.

### <a name="generate-a-property-stub"></a>Özellik saplaması oluşturma
Ürün belirtimi, `Automobile` sınıfın iki ortak özelliği `Model` olduğunu `TopSpeed`ve . Bu özellikler varsayılan değerleri `"Not specified"` ve `-1` varsayılan oluşturucu tarafından başharfle olmalıdır. Aşağıdaki birim testi, varsayılan oluşturucunun özellikleri doğru varsayılan değerlerine ayarladığını doğrular.

1. Test yöntemine aşağıdaki kod `DefaultAutomobileIsInitializedCorrectly` satırını ekleyin.

     [!code-csharp[VbTDDWalkthrough#1](../ide/codesnippet/CSharp/walkthrough-test-first-support-with-the-generate-from-usage-feature_1.cs)]
     [!code-vb[VbTDDWalkthrough#1](../ide/codesnippet/VisualBasic/walkthrough-test-first-support-with-the-generate-from-usage-feature_1.vb)]

2. Kod üzerinde `Automobile`tanımlanmamış iki özelliye başvurulduğundan, dalgalı bir alt çizgi nin altında `Model` görünür ve. `TopSpeed` Üzerinde `Model` hover ve **Hızlı Eylemler** hata ampul seçin, sonra özellik **'Automobile.Model' oluştur'u**seçin.

3. `TopSpeed` Aynı şekilde özellik için bir özellik saplaması oluşturun.

     `Automobile` Sınıfta, yeni özelliklerin türleri doğru bağlamından çıkarılır.

### <a name="generate-a-stub-for-a-new-constructor"></a>Yeni bir oluşturucu için bir saplama oluşturma
Şimdi, özellikleri `Model` ve `TopSpeed` özelliklerini başlangıç olarak oluşturmak için bir yapıcı saplama oluşturacak bir test yöntemi oluşturacağız. Daha sonra, testi tamamlamak için daha fazla kod eklersiniz.

1. Sınıfınıza aşağıdaki ek test `AutomobileTest` yöntemini ekleyin.

     [!code-csharp[VbTDDWalkthrough#2](../ide/codesnippet/CSharp/walkthrough-test-first-support-with-the-generate-from-usage-feature_2.cs)]
     [!code-vb[VbTDDWalkthrough#2](../ide/codesnippet/VisualBasic/walkthrough-test-first-support-with-the-generate-from-usage-feature_2.vb)]

2. Kırmızı dalgalı altında **Hızlı Eylemler** hata ampul tıklayın ve sonra **'Otomobil' yapıcı oluşturucu oluşturucu oluşturun'u**tıklatın.

     `Automobile` Sınıf dosyasında, yeni oluşturucunun kurucu çağrısında kullanılan yerel değişkenlerin adlarını incelediğine, `Automobile` sınıfta aynı adlara sahip özellikler bulduğuna ve bağımsız değişken değerlerini `Model` ve `TopSpeed` özelliklerinde depolamak için yapı gövdesinde kod sağladığına dikkat edin.

3. Yeni oluşturucuyu oluşturduktan sonra, 'deki varsayılan oluşturucuya çağrının `DefaultAutomobileIsInitializedCorrectly`altında dalgalı bir alt çizgi görüntülenir. Hata iletisi, `Automobile` sınıfın sıfır bağımsız değişken alan bir oluşturucusu olmadığını belirtir. Parametreleri olmayan açık bir varsayılan oluşturucu oluşturmak için **Hızlı Eylemler** hata ampulü'ne tıklayın ve ardından **'Otomobil'de oluşturucu oluştur'u tıklatın.**

### <a name="generate-a-stub-for-a-method"></a>Bir yöntem için saplama oluşturma
Belirtimin, özellikleri `Automobile` `Model` nin ve `TopSpeed` özellikleri `IsRunning` varsayılan değerlerdışında bir şeye ayarlanmışsa yeni bir duruma getirilebileceğini belirtir.

1. `AutomobileWithModelNameCanStart` Yönteme aşağıdaki satırları ekleyin.

     [!code-csharp[VbTDDWalkthrough#3](../ide/codesnippet/CSharp/walkthrough-test-first-support-with-the-generate-from-usage-feature_3.cs)]
     [!code-vb[VbTDDWalkthrough#3](../ide/codesnippet/VisualBasic/walkthrough-test-first-support-with-the-generate-from-usage-feature_3.vb)]

2. Yöntem çağrısı için **Hızlı** Hareketler `myAuto.Start` hata ampulü'ne tıklayın ve ardından **'Automobile.Start' yöntemini oluştur'u**tıklatın.

3. Özellik için **Hızlı Eylemler** `IsRunning` ampulü tıklatın ve sonra **'Automobile.IsRunning' özelliği oluştur'u**tıklatın.

     Sınıf `Automobile` şimdi adlı `Start()` bir yöntem ve `IsRunning`adlı bir özellik içerir.

### <a name="run-the-tests"></a>Testleri çalıştırma

1. **Test** menüsünde Tüm Testleri **Çalıştır'ı** > **All Tests**seçin.

     **Tüm Testleri** **Çalıştır** > komutu, geçerli çözüm için yazılmış tüm test çerçevelerinde tüm testleri çalıştırUr. Bu durumda, iki test vardır ve her ikisi de beklendiği gibi başarısız. `Assert.IsTrue` Koşul döndürür `False`çünkü `DefaultAutomobileIsInitializedCorrectly` test başarısız olur. Sınıftaki yöntem `Start` bir özel `Automobile` durum attığından `AutomobileWithModelNameCanStart` test başarısız olur.

     **Test Sonuçları** penceresi aşağıdaki resimde gösterilmiştir.

     ![Başarısız olan test sonuçları](../ide/media/testsfailed.png)

2. Test **Sonuçları** penceresinde, her testin bulunduğu yere gitmek için her test sonuç satırına çift tıklayın.

### <a name="implement-the-source-code"></a>Kaynak kodu uygulama

1. Varsayılan oluşturucuya aşağıdaki kodu ekleyin, `Model` `TopSpeed` böylece `IsRunning` , ve özelliklerin tümü doğru `"Not specified"` `-1`varsayılan `False` değerlerine `false` , ve (veya C#için) başharflere getirilmiştir.

     [!code-csharp[VbTDDWalkthrough#5](../ide/codesnippet/CSharp/walkthrough-test-first-support-with-the-generate-from-usage-feature_5.cs)]
     [!code-vb[VbTDDWalkthrough#5](../ide/codesnippet/VisualBasic/walkthrough-test-first-support-with-the-generate-from-usage-feature_5.vb)]

2. `Start` Yöntem çağrıldığında, `IsRunning` bayrağı yalnızca `Model` veya `TopSpeed` özellikler varsayılan değerden başka bir şeye ayarlanmışsa doğru olarak ayarlamalıdır. Yöntem `NotImplementedException` gövdesinden kaldırın ve aşağıdaki kodu ekleyin.

     [!code-csharp[VbTDDWalkthrough#6](../ide/codesnippet/CSharp/walkthrough-test-first-support-with-the-generate-from-usage-feature_6.cs)]
     [!code-vb[VbTDDWalkthrough#6](../ide/codesnippet/VisualBasic/walkthrough-test-first-support-with-the-generate-from-usage-feature_6.vb)]

### <a name="run-the-tests-again"></a>Testleri yeniden çalıştırın

- **Test** menüsünde **Çalıştır'ı**işaret edin ve ardından **Tüm Testler'i**tıklatın.

     Bu sefer testler geçiyor. **Test Sonuçları** penceresi aşağıdaki resimde gösterilmiştir.

     ![Geçen test sonuçları](../ide/media/testspassed.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Kullanımdan üretin](../ide/visual-csharp-intellisense.md#generate-from-usage)
- [Kod düzenleyicisinin özellikleri](../ide/writing-code-in-the-code-and-text-editor.md)
- [IntelliSense kullanma](../ide/using-intellisense.md)
- [Birim kodunuzu test edin](../test/unit-test-your-code.md)
- [Hızlı Eylemler](../ide/quick-actions.md)
