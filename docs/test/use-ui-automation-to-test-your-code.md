---
title: Kodlanmış UI testleri
ms.date: 12/04/2018
ms.topic: conceptual
f1_keywords:
- vs.codedUITest
- vs.codedUITest.recorder
- vs.codedUITest.testbuilder
- vs.codedUITest.addAssertions
- vs.codedUITest.createdialog
helpviewer_keywords:
- automated tests, testing UI interface
- coded UI test
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f333cc3409056739cef7c378d9815f10439ab37e
ms.sourcegitcommit: 5d1b2895d3a249c6bea30eb12b0ad7c0f0862d85
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80880370"
---
# <a name="use-coded-ui-test-to-test-your-code"></a>Kodunuzu test etmek için Kodlu UI testini kullanma

Kodlanmış Kullanıcı Arabirimi testleri (CUIs) uygulamanızı kullanıcı arabirimi (UI) aracılığıyla yönlendirir. Bu testler, UI denetimlerinin işlevsel testini içerir. Kullanıcı arabirimi de dahil olmak üzere tüm uygulamanın doğru çalıştığını doğrulamanızı sağlarlar. Kodlanmış Kullanıcı Arabirimi testleri, örneğin bir web sayfasında, kullanıcı arabiriminde doğrulama veya başka bir mantık varsa yararlıdır. Ayrıca, varolan bir el ile testi otomatikleştirmek için de sık lıkla kullanılır.

Visual Studio'da Kodlu UI testi oluşturmak kolaydır. **Kodlu UI Test Builder** arka planda çalışırken testi el ile gerçekleştirmeniz yeterlidir. Belirli alanlarda hangi değerlerin görünmesi gerektiğini de belirtebilirsiniz. **Kodlu UI Test Builder** eylemlerinizi kaydeder ve onlardan kod oluşturur. Sınama oluşturulduktan sonra, eylem sırasını değiştirmenize olanak tanıyan özel bir düzenleyicide bunu değiştirebilirsiniz.

Özel **Kodlu UI Test Oluşturucu** su ve düzenleyici, ana becerileriniz kodlama yerine test te yoğunlaşmış olsa bile, Kodlu UI testlerini oluşturmayı ve yönetmeyi kolaylaştırır. Ancak bir geliştiriciyseniz ve testi daha gelişmiş bir şekilde genişletmek istiyorsanız, kod kopyalanması ve uyarlanması kolay olacak şekilde yapılandırılmıştır. Örneğin, bir web sitesinden bir şey satın almak için bir test kaydedebilir ve ardından birçok öğe satın alan bir döngü eklemek için oluşturulan kodu edebilirsiniz.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="requirements"></a>Gereksinimler

- Visual Studio Enterprise
- Kodlanmış UI test bileşeni

Kodlanmış Kullanıcı Arabirimi testleri ile hangi platformların ve yapılandırmaların desteklendiği hakkında daha fazla bilgi için desteklenen [platformlara](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)bakın.

## <a name="install-the-coded-ui-test-component"></a>Kodlanmış UI test bileşenini yükleme

Kodlanmış UI test araçlarına ve şablonlarına erişmek için Visual **Studio'nun Kodlanmış UI test** bileşenini yükleyin.

1.  > **Araçlar Araç ve Özellikleri** **Tools**alın seçerek Visual **Studio Installer** başlatın.

1. **Visual Studio Installer'da,** Tek **tek bileşenleri** sekmesini seçin ve ardından **Hata Ayıklama ve Test** bölümüne gidin. **Kodlanmış UI test** bileşenini seçin.

   ![Kodlanmış UI test bileşeni](media/coded-ui-test-component.png)

1. **Değiştir'i**seçin.

## <a name="create-a-coded-ui-test"></a>Kodlu UI testi oluşturma

1. Kodlu Bir UI test projesi oluşturun.

   Kodlanmış UI testleri, Kodlu Bir UI test projesinde bulunmalıdır. Zaten Kodlu Bir UI test projeniz yoksa, bir tane oluşturun. **Dosya** > **Yeni** > **Proje'yi**seçin. **Kodlanmış UI Test Project** proje şablonunu arayın ve seçin.

   ::: moniker range="vs-2017"

   ![Yeni Proje iletişim kutusunda kodlanmış UI test projesi şablonu](media/coded-ui-test-project-template.png)

   ::: moniker-end

   > [!NOTE]
   > **Kodlanmış UI Test Project** şablonunu görmüyorsanız, [Kodlanmış UI test bileşenini yüklemeniz](../test/use-ui-automation-to-test-your-code.md#install-the-coded-ui-test-component)gerekir.

2. Kodlu UI test dosyası ekleyin.

     Kodlanmış bir UI projesi oluşturduysanız, ilk CUIT dosyası otomatik olarak eklenir. Başka bir test dosyası eklemek **için, Solution Explorer'daki**Kodlanmış UI test projesindeki kısayol menüsünü açın ve ardından**Kodlu UI Testi** **Ekle'yi** > seçin.

     **Kodlanmış UI Testi** iletişim kutusunda, Eylemleri >  **Kaydet'i**yeniden**atlaveya iddiaekleni**seçin.

     ![Kodlu UI test iletişim kutusu için kod oluşturma](media/generate-code-for-coded-ui-test.png)

     **Kodlanmış UI Test Oluşturucu** görünür.

     ![Kodlu UI Test Oluşturucu](../test/media/codedui_testbuilder.png)

3. Bir dizi eylem kaydedin.

     **Kaydetmeye başlamak için** **Kayıt** simgesini seçin. Gerekirse uygulamayı başlatmak da dahil olmak üzere, uygulamanızda sınamak istediğiniz eylemleri gerçekleştirin. Örneğin, bir web uygulamasını test ediyorsanız, bir tarayıcı başlatabilir, web sitesine gidebilir ve uygulamada oturum açabilirsiniz.

     **Kaydı duraklatmak için**, örneğin gelen postayla ilgilenmeniz gerekiyorsa, **Duraklat'ı**seçin.

    > [!WARNING]
    > Masaüstünde gerçekleştirilen tüm eylemler kaydedilir. Kayda hassas verilerin eklenmesine neden olabilecek eylemler gerçekleştirecekseniz kaydı duraklatın.

     Yanlışlıkla kaydettiğiniz **eylemleri silmek için** **Adımları Düzenle'yi**seçin.

     Eylemlerinizi çoğaltacak **kod oluşturmak** için **Kod Oluştur** simgesini seçin ve Kodlanmış Kullanıcı Arabirimi test yönteminiz için bir ad ve açıklama yazın.

4. Metin kutuları gibi Kullanıcı Arası Birimi alanlarındaki değerleri doğrulayın.

     **Kodlanmış Kullanıcı Bira**Testi Oluşturucu'da **İddialar Ekle'yi** seçin ve ardından çalışan uygulamanızda bir Kullanıcı Aracı denetimi seçin. Görünen özellikler listesinde, örneğin metin kutusundaki **Metin** gibi bir özellik seçin. Kısayol menüsünde, **İddia Ekle'yi**seçin. İletişim kutusunda, karşılaştırma işleci, karşılaştırma değeri ve hata iletisini seçin.

     İddia penceresini kapatın ve **Kod Oluştur'u**seçin.

     ![Kodlanmış UI test hedefleme öğesi](../test/media/codedui_1.png)

    > [!TIP]
    > Eylemleri kaydetme ve değerleri doğrulama arasında geçiş. Her eylem veya doğrulama dizisinin sonunda kod oluşturun. İsterseniz, daha sonra yeni eylemler ve doğrulamalar ekleyebilirsiniz.

     Daha fazla ayrıntı için [bkz.](#validate-the-properties-of-ui-controls)

5. Oluşturulan test kodunu görüntüleyin.

     Oluşturulan kodu görüntülemek için UI Test Builder penceresini kapatın. Kodda, her adıma vermiş olduğunuz adları görebilirsiniz. Kod, oluşturduğunuz CUIT dosyasında dır:

    ```csharp
    [CodedUITest]
    public class CodedUITest1
    { ...
      [TestMethod]
      public void CodedUITestMethod1()
      {
          this.UIMap.AddTwoNumbers();
          this.UIMap.VerifyResultValue();
          // To generate more code for this test, select
          // "Generate Code" from the shortcut menu.
      }
    }
    ```

6. Daha fazla eylem ve iddia ekleyin.

   İmleci test yönteminde uygun noktaya yerleştirin ve ardından kısayol menüsünde **Kodlu UI Testi için Kod Oluştur'u**seçin. Bu noktada yeni kod eklenir.

7. Test eylemlerinin ayrıntılarını ve iddiaları edin.

     Açık *UIMap.uitest*. Bu dosya, kaydettiğiniz herhangi bir eylem dizisini ve iddialarınızı da değiştirebileceğiniz **Kodlanmış UI Test**Düzenleyicisi'nde açılır.

     ![Kodlanmış UI Test Düzenleyicisi](../test/media/cuit_editor_edit.png)

     Daha fazla bilgi için, [Kodlu Kullanıcı Arabirimi Test düzenleyicisini kullanarak Kodlanmış Kullanıcı Arabirimi testlerini edit'e](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md)bakın.

8. Testi çalıştırın.

   Test Gezgini'ni kullanın veya test yönteminde kısayol menüsünü açın ve ardından **Testleri Çalıştır'ı**seçin. Testleri çalıştırma hakkında daha fazla bilgi için, bu konunun sonundaki *Kodlu Kullanıcı Arabirimi testlerini çalıştırmak için* Test Gezgini ve Ek [seçeneklerle birim testleri](../test/run-unit-tests-with-test-explorer.md) çalıştır'a [bakın.](#whats-next)

Bu konuda kalan bölümler, bu yordamdaki adımlar hakkında daha fazla ayrıntı sağlar.

Daha ayrıntılı bir örnek için, [Bkz. Walkthrough: Kodlu Bir UI testi oluşturma, düzenleme ve bakım.](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md) İzlenecek yol, kodlanmış bir kullanıcı arama caymı testi oluşturma, yönetme ve koruma yı göstermek için basit bir Windows Sunu Temeli (WPF) uygulaması oluşturursunuz. İzlenecek yol çeşitli zamanlama sorunları ve yeniden düzenlemeyi denetleme tarafından kırılan testleri düzeltmeye ilişkin çözümler sağlar.

## <a name="start-and-stop-the-application-under-test"></a>Test altında uygulamayı başlatın ve durdurun

Her test için uygulamayı, tarayıcıyı veya veritabanını ayrı ayrı başlatmak ve durdurmak istemiyorsanız, aşağıdakilerden birini yapın:

- Uygulamanızı test altında başlatmak için yapılan eylemleri kaydetmek istemiyorsanız, **Kayıt** simgesini seçmeden önce uygulamanızı başlatmanız gerekir.

- Bir testin sonunda, testin çalıştırıldığı işlem sonlandırılır. Uygulamanızı testte başlattıysanız, uygulama genellikle kapanır.  Testin uygulamanızdan çıktığında kapanmasını istemiyorsanız, çözüme bir *.runsettings* dosyası ekleyin ve `KeepExecutorAliveAfterLegacyRun` seçeneği kullanın. Daha fazla bilgi için [bkz.](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)

- Her test yönteminin başında kod `[TestInitialize]` çalıştıran bir öznitelik tarafından tanımlanan bir test başlatma yöntemi ekleyin. Örneğin, uygulamayı TestInitialize yönteminden başlatabilirsiniz.

- Her test yönteminin sonunda kod `[TestCleanup]` çalıştıran bir öznitelik tarafından tanımlanan bir test temizleme yöntemi ekleyin. Örneğin, uygulamayı kapatma yöntemi TestCleanup yönteminden çağrılabilir.

## <a name="validate-the-properties-of-ui-controls"></a>UI denetimlerinin özelliklerini doğrulama

**Kodlanmış Kullanıcı Arabirimi Test** Oluşturucusu'nu, testiniz için [UIMap'e](/previous-versions/dd580454(v=vs.140)) bir kullanıcı arabirimi (UI) denetimi eklemek veya kullanıcı arabirimi denetimi için bir sedik kullanan bir doğrulama yöntemi için kod oluşturmak için kullanabilirsiniz.

Kullanıcı Arabirimi denetimleriniz için iddialar oluşturmak için, **Kodlanmış Kullanıcı Arabirimi Test Oluşturucusu'ndaki** **İddialar Ekle** aracını seçin ve doğrulamak istediğiniz test altındaki uygulama üzerindeki denetime sürükleyin. Kutu denetiminizi özetlediğinde fareyi serbest bırakın. Denetim sınıfı kodu *hemen UIMap.Designer.cs* dosyasında oluşturulur.

![Kodlanmış UI test hedefleme öğesi](../test/media/codedui_1.png)

Bu denetimin özellikleri artık **Ekler Ek** iletişim kutusunda listelenmiştir.

Belirli bir denetime gezinmenin başka bir yolu, **UI Denetim Haritası'nın**görünümünü genişletmek için oku **(<<)** seçmektir. Bir ebeveyn, kardeş veya alt denetim bulmak için haritanın herhangi bir yerine tıklayabilir ve ağacın etrafında hareket etmek için ok tuşlarını kullanabilirsiniz.

![Kodlanmış UI test özellikleri](../test/media/codedui_2.png)

> [!TIP]
> Uygulamanızda bir denetim seçtiğinizde herhangi bir özellik görmüyorsanız veya UI Denetim Haritası'ndaki denetimi görmüyorsanız, denetimin uygulama kodunda benzersiz bir kimliği olduğunu doğrulayın. Benzersiz kimlik, HTML kimlik özniteliği veya WPF UId olabilir.

Ardından, doğrulamak istediğiniz UI denetimi için özellikteki kısayol menüsünü açın ve ardından **İddia Ekle'yi**işaret edin. İddia **Ekle** iletişim kutusunda, örneğin iddianızın <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A> **Karşılaştırıcısını** seçin ve **karşılaştırma değeri'ndeki**iddianızın değerini yazın.

![Kodlanmış UI test iddiaları](../test/media/codedui_3.png)

Testiniz için tüm iddialarınızı eklediyseniz, **Tamam'ı**seçin.

İddialarınızın kodunu oluşturmak ve denetimi UI eşlemi'ne eklemek için **Kod Oluştur** simgesini seçin. Kodlanmış Kullanıcı Arabirimi test yönteminiz için bir ad ve yöntem için açıklama olarak eklenecek bir açıklama yazın. **Ekle ve Oluştur'u**seçin. Ardından, **Kodlanmış UI Test Oluşturucusu'nu**kapatmak için **Kapat** simgesini seçin. Bu, aşağıdaki koda benzer kod oluşturur. Örneğin, girdiğiniz ad `AssertForAddTwoNumbers`, kod aşağıdaki örneğe benzer:

- Kodlanmış UI test dosyanızdaki test yöntemine AssertForAddTwoNumbers'a bir çağrı ekler:

    ```csharp
    [TestMethod]
    public void CodedUITestMethod1()
    {
        this.UIMap.AddTwoNumbers();
        this.UIMap.AssertForAddTwoNumbers();
    }
    ```

     Adımların ve iddiaların sırasını değiştirmek veya yeni test yöntemleri oluşturmak için bu dosyayı düzenleyebilirsiniz. Daha fazla kod eklemek için imleci test yöntemine yerleştirin ve kısayol menüsüne **Kodlu UI Testi için Kod Oluştur'u**seçin.

- UI haritanıza `AssertForAddTwoNumbers` *(UIMap.uitest)* çağrılan bir yöntem ekler. Bu dosya, iddiaları değiştirebileceğiniz **Kodlanmış UI Test**Düzenleyicisi'nde açılır.

     ![Kodlu UI test Düzenleyicisi'ni kullanarak öne sözü belirleme](../test/media/cuit_editor_assert.png)

     Daha fazla bilgi için, [Kodlu Kullanıcı Arabirimi test düzenleyicisini kullanarak Kodlanmış Kullanıcı Arabirimi testlerini edit'e](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md)bakın.

     Ayrıca *UIMap.Designer.cs'da*seince yönteminin oluşturulan kodunu görüntüleyebilirsiniz. Ancak, bu dosyayı da Kodun uyarlanmış bir sürümünü yapmak istiyorsanız, yöntemleri *UIMap.cs*gibi başka bir dosyaya kopyalayın, yöntemleri yeniden adlandırın ve burada edin.

    ```csharp
    public void AssertForAddTwoNumbers()
    {
        ...
    }
    ```

### <a name="select-a-hidden-control-using-the-keyboard"></a>Klavyeyi kullanarak gizli bir denetim seçin

Seçmek istediğiniz denetim odağı kaybederse ve **Kodlanmış UI Test Oluşturucu'dan** **Ekler Ekler** aracını seçtiğinizde kaybolur:

Bazen, denetimler eklediğinizde ve özelliklerini doğruladığınızda, klavyeyi kullanmanız gerekebilir. Örneğin, sağ tıklatma menüsü denetimini kullanan kodlanmış bir ui testi kaydetmeye çalıştığınızda, **kodlanmış UI Test Oluşturucusu'ndan** **Bağımsız Sonuç Ekle** aracını seçmeye çalıştığınızda denetimdeki menü öğelerinin listesi odağı kaybeder ve kaybolur. Bu, Internet Explorer'daki sağ tıklama menüsünün odak noktasını kaybettiği ve **İddia ekle** aracıyla seçmeye çalıştığınızda kaybolduğu aşağıdaki resimde gösterilmiştir.

![CodedUITest&#95;SelectControlKeyboard](../test/media/codeduitest_selectcontrolkeyboard.png)

UI denetimini seçmek için klavyeyi kullanmak için fareyle denetimin üzerine inin. Sonra **Ctrl** tuşunu ve **I** tuşunu aynı anda basılı tutun. Anahtarları serbest bırak. Denetim **Kodlanmış UI Test Builder**tarafından kaydedilir.

#### <a name="manually-record-mouse-hovers"></a>Fare gezinmelerini el ile kaydetme

Bir fareyi bir denetimüzerinde kaydedemezseniz:

Bazı durumlarda, Kodlu UI testinde kullanılan belirli bir denetim, fare gezinme olaylarını el ile kaydetmek için klavyeyi kullanmanızı gerektirebilir. Örneğin, bir Windows Formunu veya Windows Sunu Temeli (WPF) uygulamasını sınadiğinizde, özel kod olabilir. Veya, bir kullanıcı üzerinde gezinirken genişleyen bir ağaç düğümü gibi bir denetimüzerinde gezinmek için tanımlanmış özel bir davranış olabilir. Bu gibi durumları test etmek için, önceden tanımlanmış klavye tuşlarına basarak denetimüzerinde gezindiğinizi **Kodlanmış UI Test Builder'a** el ile bildirmeniz gerekir.

Kodlu UI testinizi gerçekleştirirken, denetimin üzerine girin. Daha sonra **Ctrl**tuşuna basın ve basılı tutun, klavyenizde **Shift** ve **R** tuşlarına basıp basılı tutun. Anahtarları serbest bırak. Bir fare gezinme olayı **Kodlanmış UI Test Builder**tarafından kaydedilir.

![CodedUI&#95;Hover](../test/media/codedui_hover.png)

Test yöntemini oluşturduktan sonra, aşağıdaki örneğe benzer kod *UIMap.Designer.cs* dosyasına eklenir:

```csharp
// Mouse hover '1' label at (87, 9)
Mouse.Hover(uIItem1Text, new Point(87, 9));
```

### <a name="configure-mouse-hover-keyboard-assignments"></a>Fare-hover klavye atamalarını yapılandırma

Fare gezinme olaylarını yakalamak için anahtar atama ortamımın başka bir yerinde kullanılıyorsa:

Gerekirse, Kodlu UI testlerinizde fare gezinme olaylarını uygulamak için kullanılan **Ctrl**+**Shift**+**R'nin** varsayılan klavye ataması farklı tuşları kullanacak şekilde yapılandırılabilir.

> [!WARNING]
> Sıradan koşullar altında fare gezinme olayları için klavye atamaları değiştirmek zorunda olmamalıdır. Klavye atamasını yeniden atarken dikkatli olun. Seçiminiz visual studio içinde başka bir yerde veya test edilen uygulama zaten kullanımda olabilir.

Klavye atamalarını değiştirmek için aşağıdaki yapılandırma dosyasını değiştirin:

*%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CodedUITestBuilder.exe.config*

Yapılandırma dosyasında, klavye atamalarını `HoverKeyModifier` `HoverKey` değiştirmek için tuşların ve tuşların değerlerini değiştirin:

```xml
<!-- Begin : Background Recorder Settings -->
<!-- HoverKey to use. -->
<add key="HoverKeyModifier" value="Control, Shift"/>
<add key="HoverKey" value="R"/>
```

### <a name="set-implicit-mouse-hovers-for-the-web-browser"></a>Web tarayıcısı için örtülü fare gezinmelerini ayarlama

Bir web sitesinde fare gezinmelerini kaydetmede sorun yaşıyorsanız:

Birçok web sitesinde, belirli bir denetimin üzerinde gezinirken, ek ayrıntılar göstermek için genişletir. Genellikle, bu masaüstü uygulamalarında menüler gibi görünür. Bu yaygın bir desen olduğundan, Kodlu UI testleri web'de gezinmek için örtülü gezinmeleri sağlar. Örneğin, Internet Explorer'da gezinme kaydederseniz, bir olay ateşlenir. Bu olaylar gereksiz gezinmelerin kaydedilmesine neden olabilir. Bu nedenle, örtük gezinmeler UI `true` test yapılandırma dosyasına ayarlanmış olarak `ContinueOnError` kaydedilir. Bu, gezinme olayı başarısız olursa oynatmanın devam etmesine olanak tanır.

Bir web tarayıcısında örtülü gezinmelerin kaydedilmesini etkinleştirmek için yapılandırma dosyasını açın:

*%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CodedUITestBuilder.exe.config*

Yapılandırma dosyasının aşağıdaki örnekte gösterildiği `RecordImplicitiHovers` `true` gibi bir değer eki anahtar kümesine sahip olduğunu doğrulayın:

```xml
<!--Use this to enable/disable recording of implicit hovers.-->
<add key="RecordImplicitHover" value="true"/>
```

## <a name="customize-the-coded-ui-test"></a>Kodlu UI testini özelleştirme

Kodlu UI testinizi oluşturduktan sonra Visual Studio'da aşağıdaki araçlardan birini kullanarak bunu değiştirebilirsiniz:

- Testlerinize ek denetimler ve doğrulama eklemek için **Kodlu UI Test Builder'ı** kullanın. Denetimler ekle ve bu [konudaki özelliklerini doğrula](#validate-the-properties-of-ui-controls) bölümüne bakın.

- **Kodlanmış UI Test** Düzenleyicisi, Kodlu UI testlerinizi kolayca değiştirmenizi sağlar. **Kodlu UI Test Düzenleyicisi'ni**kullanarak test yöntemlerinizi bulabilir, görüntüleyebilir ve değiştirebilirsiniz. UI denetim haritasında ui eylemlerini ve bunların ilişkili denetimlerini de edinebilirsiniz. Daha fazla bilgi için, [Kodlu Kullanıcı Arabirimi test düzenleyicisini kullanarak Kodlanmış Kullanıcı Arabirimi testlerini edit'e](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md)bakın.

- **Kod Düzenleyicisi:**

  - Bu konudaki [Kodlanmış UI denetim eylemleri ve özellikleri](#coded-ui-control-actions-and-properties) bölümünde açıklandığı gibi testinizdeki denetimler için el ile kod ekleyin.

  - Kodlanmış bir UI testi oluşturduktan sonra, bunu veri tabanlı olacak şekilde değiştirebilirsiniz. Daha fazla bilgi için [bkz.](../test/creating-a-data-driven-coded-ui-test.md)

  - Kodlu UI test oynatma oyununda, teste pencerenin görünmesi, ilerleme çubuğunun kaybolması gibi belirli olayların oluşmasını beklemesini öğretebilirsiniz. Bunu yapmak için, uygun UITestControl.WaitForControlXXX() yöntemini ekleyin. Kullanılabilir yöntemlerin tam listesi için bkz. [kodlanmış UI testleri oynatma sırasında belirli olayları bekletin.](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md) WaitForControlEnabled yöntemini kullanarak denetimin etkinleştirilmesini bekleyen Kodlanmış UI testi örneği [için](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)bkz.

  - Kodlanmış UI testleri, Internet Explorer 9 ve Internet Explorer 10'da bulunan HTML5 denetimlerinden bazılarının desteğini içerir. Daha fazla bilgi için bkz: [Kodlanmış Kullanıcı Arabirimi testlerinde HTML5 denetimlerini kullanma.](../test/using-html5-controls-in-coded-ui-tests.md)

  - Kodlanmış UI test kodlama kılavuzu:

    - [Kodlanmış ui testinin anatomisi](../test/anatomy-of-a-coded-ui-test.md)

    - [Kodlanmış Ara Birimi testleri için en iyi uygulamalar](../test/best-practices-for-coded-ui-tests.md)

    - [Birden çok Kullanıcı Altı Bilgi Yle büyük bir uygulamayı test edin](../test/testing-a-large-application-with-multiple-ui-maps.md)

    - [Kodlanmış UI testleri ve eylem kayıtları için desteklenen yapılandırmalar ve platformlar](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)

### <a name="the-generated-code"></a>Oluşturulan kod

**Kodu Oluştur'u**seçtiğinizde, birkaç kod parçası oluşturulur:

- Test yönteminde bir satır.

    ```csharp
    [CodedUITest]
    public class CodedUITest1
    { ...
      [TestMethod]
      public void CodedUITestMethod1()
      {
          this.UIMap.AddTwoNumbers();
          // To generate more code for this test, select
          // "Generate Code" from the shortcut menu.      }
    }
    ```

     Daha fazla kaydedilmiş eylem ve doğrulama eklemek için bu yönteme sağ tıklayabilirsiniz. Kodu genişletmek veya değiştirmek için el ile de değiştirebilirsiniz. Örneğin, kodun bir kısmını bir döngüye ekleyebilirsiniz.

     Ayrıca, yeni test yöntemleri ekleyebilir ve bunlara aynı şekilde kod ekleyebilirsiniz. Her test yöntemi `[TestMethod]` özniteliğe sahip olmalıdır.

- *UIMap.uitest*bir yöntem .

     Bu yöntem, kaydettiğiniz eylemlerin ayrıntılarını veya doğruladığınız değeri içerir. *UIMap.uitest'i*açarak bu kodu edinebilirsiniz. Kaydedilen eylemleri silebileceğiniz veya yeniden kaldırabileceğiniz özel bir düzenleyicide açılır.

     Oluşturulan yöntemi *UIMap.Designer.cs*olarak da görüntüleyebilirsiniz. Bu yöntem, testi çalıştırdığınızda kaydettiğiniz eylemleri gerçekleştirir.

    ```csharp
    // File: UIMap.Designer.cs
    public partial class UIMap
    {
      /// <summary>
      /// Add two numbers
      /// </summary>
      public void AddTwoNumbers()
      { ...   }
    }
    ```

    > [!WARNING]
    > Daha fazla test oluşturduğunuzda yeniden oluşturulacağı için bu dosyayı kaldırmamalısınız.

     Bu yöntemlerin uyarlanmış sürümlerini *UIMap.cs*kopyalayarak yapabilirsiniz. Örneğin, bir test yönteminden arayabilirsiniz parametreli bir sürümünü yapabilirsiniz:

    ```csharp
    // File: UIMap.cs
    public partial class UIMap // Same partial class
    {
      /// <summary>
      /// Add two numbers - parameterized version
      /// </summary>
      public void AddTwoNumbers(int firstNumber, int secondNumber)
      { ...   // Code modified to use parameters.
      }
    }
    ```

- *UIMap.uitest'teki*bildirimler.

    Bu bildirimler, testiniz tarafından kullanılan uygulamanın Kullanıcı Bire-posta denetimlerini temsil eder. Bunlar, denetimleri çalıştırmak ve özelliklerine erişmek için oluşturulan kod tarafından kullanılır.

    Kendi kodunuzu yazarsanız da kullanabilirsiniz. Örneğin, test yönteminizin bir web uygulamasında bir köprü seçmesine, metin kutusuna bir değer yazıp dallarını kapatmasına ve bir alandaki değere dayalı farklı test eylemleri almasını sağlayabilirsiniz.

    Büyük bir uygulamayı test etmeyi kolaylaştırmak için birden çok Kodlu Kullanıcı Arabirimi testi ve birden çok Kullanıcı Arabirimi eşlemi nesneleri ve dosyaları ekleyebilirsiniz. Daha fazla bilgi için bkz: [Birden çok Kullanıcı Arabirimi Eşlemi içeren büyük bir uygulamayı test edin.](../test/testing-a-large-application-with-multiple-ui-maps.md)

Oluşturulan kod hakkında daha fazla bilgi [için, kodlanmış bir Kullanıcı Arabirimi testinin Anatomisi'ne](../test/anatomy-of-a-coded-ui-test.md)bakın.

## <a name="coded-ui-control-actions-and-properties"></a>Kodlanmış UI denetim eylemleri ve özellikleri

Kodlu UI testlerinde UI test denetimleriyle çalışırken bunlar iki bölüme ayrılır: eylemler ve özellikler.

- İlk bölüm, UI test denetimlerinde gerçekleştirebileceğiniz eylemlerden oluşur. Örneğin, Kodlanmış UI testleri, ui test denetiminde fare tıklamalarını simüle edebilir veya bir UI test denetimini etkilemek için klavyede yazılan tuşları simüle edebilir.

- İkinci bölüm, bir UI test denetiminde özellikleri almanızı ve ayarlamanızı sağlamaktan oluşur. Örneğin, Kodlanmış UI testleri, bir `ListBox`'deki öğelerin `CheckBox` sayısını alabilir veya seçili duruma ayarlayabilir.

**UI Test Denetimi'nin Eylemlerine Erişim**

Fare tıklamaları veya klavye eylemleri gibi UI test denetimlerinde eylemler <xref:Microsoft.VisualStudio.TestTools.UITesting.Mouse> gerçekleştirmek <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard> için, ve sınıflardaki yöntemleri kullanın:

- UI test denetiminde fare tıklaması gibi fare yönelimli bir <xref:Microsoft.VisualStudio.TestTools.UITesting.Mouse.Click%2A>eylem gerçekleştirmek için.

     `Mouse.Click(buttonCancel);`

- Bir edit denetimine yazmak gibi klavye yönelimli bir <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard.SendKeys%2A>eylem gerçekleştirmek için .

     `Keyboard.SendKeys(textBoxDestination, @"C:\Temp\Output.txt");`

**UI Test Denetiminin Özelliklerine Erişim**

Kullanıcı Arabirimi denetimibelirli özellik değerlerini almak ve ayarlamak için, bir denetimin özelliklerini doğrudan <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A?displayProperty=fullName> alabilir <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A?displayProperty=fullName> veya ayarlayabilir veya istediğiniz belirli özelliğin adı ile ve yöntemleri kullanabilirsiniz.

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A>daha sonra uygun <xref:System.Type>döküm olabilir bir nesne, döndürür. <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A>özelliğin değeri için bir nesne kabul eder.

### <a name="to-get-or-set-properties-from-ui-test-controls-directly"></a>Doğrudan UI test denetimlerinden özellikleri almak veya ayarlamak için

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl> [HtmlList](xref:Microsoft.VisualStudio.TestTools.UITesting.HtmlControls.HtmlList) veya [WinComboBox](xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls.WinComboBox)gibi denetimlerden türeyen denetimlerle, özellik değerlerini doğrudan alabilir veya ayarlayabilirsiniz. Aşağıdaki kod bazı örnekleri gösterir:

```csharp
int i = myHtmlList.ItemCount;
myWinCheckBox.Checked = true;
```

### <a name="to-get-properties-from-ui-test-controls"></a>UI test denetimlerinden özellikler almak için

- Bir denetimden özellik değeri elde <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A>etmek için .

- Almak için denetimin özelliğini belirtmek için, `PropertyNames` <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A>her denetimdeki sınıftaki uygun dizeyi parametre olarak kullanın.

- <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A>uygun veri türünü döndürür, ancak bu <xref:System.Object>iade değeri . İade <xref:System.Object> daha sonra uygun tür olarak döküm gerekir.

     Örnek:

     `int i = (int)GetProperty(myHtmlList.PropertyNames.ItemCount);`

### <a name="to-set-properties-for-ui-test-controls"></a>UI test denetimleri için özellikleri ayarlamak için

- Bir özelliği denetimde ayarlamak <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A>için .

- Ayarlamak için denetimin özelliğini belirtmek için, `PropertyNames` <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A>ikinci parametre olarak özellik değeri ile ilk parametre olarak sınıftan uygun dize kullanın.

     Örnek:

     `SetProperty(myWinCheckBox.PropertyNames.Checked, true);`

## <a name="debug"></a>Hata ayıklama

Kodlu UI test günlüklerini kullanarak Kodlu UI testlerini çözümleyebilirsiniz. Kodlanmış Kullanıcı Bira Test günlükleri filtreve Kodlu Kullanıcı Bira test çalışır hakkında önemli bilgileri kaydedin. Günlüklerin biçimi, sorunları hızlı bir şekilde hata ayıklamanızı sağlar. Daha fazla bilgi için bkz: [Kodlanmış Kullanıcı Arabirimi test günlüklerini kullanarak kodlanmış Kullanıcı Arabirimi testlerini çözümle.](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md)

## <a name="whats-next"></a>Sırada ne var?

::: moniker range="vs-2017"
**Kodlu UI testlerini çalıştırmak için ek seçenekler:** Bu konuda daha önce açıklandığı gibi Kodlu UI testlerini doğrudan Visual Studio'dan çalıştırabilirsiniz. Ayrıca, Microsoft Test Yöneticisi'nden veya Azure Denetim Hatları'nı kullanarak otomatik ui testleri çalıştırabilirsiniz. Kodlanmış UI testleri otomatik olduğunda, diğer otomatik testlerin aksine, bunları çalıştırdığınızda masaüstüyle etkileşime girmeleri gerekir.
::: moniker-end
::: moniker range=">=vs-2019"
**Kodlu UI testlerini çalıştırmak için ek seçenekler:** Bu konuda daha önce açıklandığı gibi Kodlu UI testlerini doğrudan Visual Studio'dan çalıştırabilirsiniz. Ayrıca, Azure Denetim Hatları'nı kullanarak otomatik leştirilmiş ui testleri çalıştırabilirsiniz. Kodlanmış UI testleri otomatik olduğunda, diğer otomatik testlerin aksine, bunları çalıştırdığınızda masaüstüyle etkileşime girmeleri gerekir.
::: moniker-end

- [Test Gezgini ile birim testleri çalıştırma](../test/run-unit-tests-with-test-explorer.md)

- [Yapı sürecinizde testleri çalıştırma](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts)

- [Nasıl kullanılır: Test aracınızı masaüstüyle etkileşimde olan testleri çalıştıracak şekilde ayarlama](https://msdn.microsoft.com/Library/3a94dd07-6d17-402c-ae8f-7947143755c9)

**Özel denetimler için destek ekleme:**  Kodlanmış UI sınama çerçevesi olası her ui'yi desteklemez ve test etmek istediğiniz UI'yi desteklemeyebilir. Örneğin, Microsoft Excel için hemen UI kodlu bir ui testi oluşturamazsınız. Ancak, özel denetim destekleyen Kodlanmış Kullanıcı Aracı test çerçevesiiçin bir uzantı oluşturabilirsiniz.

- [Denetimlerinizin kodlanmış UI testini etkinleştirme](../test/enable-coded-ui-testing-of-your-controls.md)

- [Kodlanmış UI testlerini ve eylem kayıtlarını genişletme](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)

Kodlanmış UI testleri genellikle el ile yapılan testleri otomatikleştirmek için kullanılır. Otomatik testler hakkında daha fazla bilgi için [Visual Studio'daki Test araçlarına](../test/improve-code-quality.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [El ile testleri kaydetme ve oynatma](/azure/devops/test/mtm/record-play-back-manual-tests?view=vsts)
- [Xamarin.UITest](/appcenter/test-cloud/uitest/)
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>
- [Walkthrough: Kodlanmış Bir UI testi oluşturun, edin ve koruyun](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
- [UWP uygulamasını test etmek için Kodlanmış UI testi oluşturma](test-uwp-app-with-coded-ui-test.md)
- [Kodlu UI testinin anatomisi](../test/anatomy-of-a-coded-ui-test.md)
- [Kodlu AraBirimi testleri için en iyi uygulamalar](../test/best-practices-for-coded-ui-tests.md)
- [Birden çok Kullanıcı Altı Bilgi Yle büyük bir uygulamayı test edin](../test/testing-a-large-application-with-multiple-ui-maps.md)
