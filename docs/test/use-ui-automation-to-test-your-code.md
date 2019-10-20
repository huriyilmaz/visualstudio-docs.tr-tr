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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5a6491a6b9ac9312befbf0c8c6c3fb0f293885ee
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659871"
---
# <a name="use-coded-ui-test-to-test-your-code"></a>Kodunuzu test etmek için kodlanmış UI testi kullanın

Kodlanmış UI testleri (CUITs) uygulamanızın kullanıcı arabirimi (UI) aracılığıyla sürüşü. Bu sınamalar, UI denetimlerinin işlevsel sınamasını içerir. Bu kişiler, Kullanıcı arabirimi de dahil olmak üzere tüm uygulamanın doğru şekilde çalıştığını doğrulamanızı sağlar. Kodlanmış UI testleri, Kullanıcı arabiriminde, örneğin bir Web sayfasında doğrulama veya başka bir mantık olduğunda faydalıdır. Ayrıca, var olan bir el ile testi otomatikleştirmek için sık kullanılır.

Visual Studio 'da kodlanmış UI testi oluşturmak kolaydır. **KODLANMıŞ UI Test Oluşturucusu** arka planda çalışırken testi yalnızca el ile gerçekleştirirsiniz. Ayrıca, belirli alanlarda görüntülenecek değerleri de belirtebilirsiniz. **KODLANMıŞ UI Test Oluşturucusu** eylemlerinizi kaydeder ve bunlardan kod oluşturur. Test oluşturulduktan sonra, eylem dizisini değiştirmenize olanak sağlayan özelleştirilmiş bir düzenleyicide düzenleyebilirsiniz.

Özelleştirilmiş **KODLANMıŞ UI Test Oluşturucusu** ve düzenleyici, kodlanmış UI testlerini oluşturmayı ve düzenlemenizi kolaylaştırır, bu da ana becerilerinizi kodlama yerine test halinde yoğunlaşdı. Ancak bir geliştiricisiyseniz ve testi daha gelişmiş bir şekilde genişletmek istiyorsanız, kod yapılandırılmıştır ve uyarlanabilmesi için yapılandırılır. Örneğin, bir Web sitesinde bir şey satın almak için bir test kaydedebilir ve sonra çok sayıda öğe alan bir döngü eklemek için oluşturulan kodu düzenleyebilirsiniz.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="requirements"></a>Gereksinimler

- Visual Studio Enterprise
- Kodlanmış UI test bileşeni

Kodlanmış UI testleri tarafından desteklenen platformlar ve Konfigürasyonlar hakkında daha fazla bilgi için bkz. [Desteklenen platformlar](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md).

## <a name="install-the-coded-ui-test-component"></a>Kodlanmış UI test bileşenini yükler

Kodlanmış UI test araçlarına ve şablonlarına erişmek için, Visual Studio 'nun **KODLANMıŞ UI test** bileşenini yükler.

1. Araçlar**ve Özellikler al** >  **araçlar** 'ı seçerek **Visual Studio yükleyicisi** başlatın.

1. **Visual Studio yükleyicisi**, **tek tek bileşenler** sekmesini seçin ve ardından aşağı kaydırarak **hata ayıklama ve test** bölümüne gidin. **KODLANMıŞ UI test** bileşeni seçin.

   ![Kodlanmış UI test bileşeni](media/coded-ui-test-component.png)

1. **Değiştir**'i seçin.

## <a name="create-a-coded-ui-test"></a>Kodlanmış UI testi oluşturma

1. Kodlanmış UI test projesi oluşturun.

   Kodlanmış UI testleri kodlanmış UI testi projesinde bulunmalıdır. Zaten kodlanmış bir UI test projeniz yoksa, bir tane oluşturun. **Dosya**  > **Yeni**  > **Proje**' yi seçin. **KODLANMıŞ UI test projesi** proje şablonunu arayın ve seçin.

   ::: moniker range="vs-2017"

   ![Yeni proje iletişim kutusunda kodlanmış UI testi proje şablonu](media/coded-ui-test-project-template.png)

   ::: moniker-end

   > [!NOTE]
   > **KODLANMıŞ UI testi proje** şablonunu görmüyorsanız, [kodlanmış UI test bileşenini yüklemeniz](../test/use-ui-automation-to-test-your-code.md#install-the-coded-ui-test-component)gerekir.

2. Kodlanmış UI test dosyası ekleyin.

     Yalnızca kodlanmış bir UI projesi oluşturduysanız, ilk CUIT dosyası otomatik olarak eklenir. Başka bir test dosyası eklemek için, **Çözüm Gezgini**' de kodlanmış UI testi projesinde kısayol menüsünü açın ve ardından  > **kodlanmış UI testi** **Ekle** ' yi seçin.

     **KODLANMıŞ UI testi Için kod üret** iletişim kutusunda,**Kullanıcı arabirimi eşlemesini Düzenle** >  **eylemleri kaydet** ' i seçin veya onaylama ekleyin.

     ![Kodlanmış UI testi iletişim kutusu için kod oluştur](media/generate-code-for-coded-ui-test.png)

     **KODLANMıŞ UI Test Oluşturucusu** görüntülenir.

     ![Kodlanmış UI Test Oluşturucusu](../test/media/codedui_testbuilder.png)

3. Bir dizi eylemi kaydedin.

     **Kaydı başlatmak Için** **kayıt** simgesini seçin. Uygulamanızda test etmek istediğiniz eylemleri, bu gerekliyse uygulamayı başlatma dahil olmak üzere gerçekleştirin. Örneğin, bir Web uygulamasını test ediyorsanız, bir tarayıcı başlatabilir, Web sitesine gidebilir ve uygulamada oturum açmanız gerekebilir.

     **Kaydı duraklatmak için**Örneğin, gelen posta ile uğraşmanız gerekiyorsa, **Duraklat**' ı seçin.

    > [!WARNING]
    > Masaüstünde gerçekleştirilen tüm eylemler kaydedilir. Kayıt sırasında hassas verilerin oluşmasına neden olabilecek eylemler gerçekleştiriyorsanız kaydı duraklatın.

     Yanlışlıkla kaydettiğiniz **eylemleri silmek Için** **adımları Düzenle**' yi seçin.

     Eylemlerinizi çoğaltan **kodu oluşturmak Için** **kod oluştur** SIMGESINI seçin ve kodlanmış UI Test yönteminiz için bir ad ve açıklama yazın.

4. Metin kutuları gibi kullanıcı arabirimi alanlarındaki değerleri doğrulayın.

     **KODLANMıŞ UI Test Oluşturucusu**'Nda **onaylama Ekle** ' yi seçin ve ardından çalışan uygulamanızda bir UI denetimi seçin. Görüntülenen özellikler listesinde, bir metin kutusundaki **metin** gibi bir özellik seçin. Kısayol menüsünde **onay Ekle**' yi seçin. İletişim kutusunda karşılaştırma işlecini, karşılaştırma değerini ve hata iletisini seçin.

     Onaylama penceresini kapatın ve **kod üret**' i seçin.

     ![Kodlanmış UI test hedefleme öğesi](../test/media/codedui_1.png)

    > [!TIP]
    > Kaydetme eylemleri ve değerleri doğrulama arasında alternatif. Her eylem veya doğrulama dizisinin sonunda kod oluşturun. İsterseniz, yeni eylemleri ve doğrulamaları daha sonra ekleyebileceksiniz.

     Daha ayrıntılı bilgi için bkz. [denetimlerin özelliklerini doğrulama](#validate-the-properties-of-ui-controls).

5. Oluşturulan test kodunu görüntüleyin.

     Oluşturulan kodu görüntülemek için UI Test Oluşturucusu penceresini kapatın. Kodda, her bir adıma verdiğiniz adları görebilirsiniz. Kod, oluşturduğunuz CUIT dosyasında bulunur:

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

6. Daha fazla eylem ve onaylama ekleyin.

   İmleci test yönteminde uygun noktaya yerleştirin ve ardından kısayol menüsünde, **KODLANMıŞ UI testi Için kod üret**' i seçin. Yeni kod bu noktaya eklenecektir.

7. Test eylemlerinin ve onayların ayrıntılarını düzenleyin.

     *UIMap. UITest*öğesini açın. Bu dosya, **KODLANMıŞ UI Test Düzenleyicisi**'nde açılır. burada, kaydettiğiniz herhangi bir işlem dizisini düzenleyebilir ve onaylarınızı düzenleyebilirsiniz.

     ![Kodlanmış UI Test Düzenleyicisi](../test/media/cuit_editor_edit.png)

     Daha fazla bilgi için bkz. [kodlanmış UI test düzenleyicisini kullanarak KODLANMıŞ UI testlerini düzenleme](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).

8. Testi çalıştırın.

   Test Gezgini 'ni kullanın veya test yönteminde kısayol menüsünü açın ve **Testleri Çalıştır**' ı seçin. Testlerin nasıl çalıştırılacağı hakkında daha fazla bilgi için, bkz. [Test Gezgini ile birim testlerini çalıştırma](../test/run-unit-tests-with-test-explorer.md) ve bu konunun sonundaki [sonraki nedir?](#whats-next) bölümünde *kodlanmış UI testlerini çalıştırmak için ek seçenekler* .

Bu konudaki geri kalan bölümler, bu yordamdaki adımlar hakkında daha fazla ayrıntı sağlar.

Daha ayrıntılı bir örnek için bkz. [Izlenecek yol: kodlanmış BIR UI testi oluşturma, düzenlemeyle ve sürdürme](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md). İzlenecek yolda, kodlanmış UI testinin nasıl oluşturulduğunu, düzenleneceğini ve bakımının nasıl yapılacağını göstermek için basit bir Windows Presentation Foundation (WPF) uygulaması oluşturacaksınız. İzlenecek yol çeşitli zamanlama sorunları ve yeniden düzenlemeyi denetleme tarafından kırılan testleri düzeltmeye ilişkin çözümler sağlar.

## <a name="start-and-stop-the-application-under-test"></a>Test edilen uygulamayı başlatma ve durdurma

Her test için uygulama, tarayıcı veya veritabanını ayrı olarak başlatıp durdurmak istemiyorsanız, aşağıdakilerden birini yapın:

- Uygulamanızı test altına başlatmak üzere eylemleri kaydetmek istemiyorsanız, **kayıt** simgesini seçmeden önce uygulamanızı başlatmanız gerekir.

- Testin sonunda, testin çalıştırıldığı işlem sonlandırılır. Uygulamanızı testte başlattıysanız uygulama genellikle kapanır.  Testin çıkılırken uygulamanızı kapatmasını istemiyorsanız, çözümünüze bir *. runsettings* dosyası ekleyin ve `KeepExecutorAliveAfterLegacyRun` seçeneğini kullanın. Daha fazla bilgi için bkz [. runsettings dosyasını kullanarak birim testlerini yapılandırma](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).

- Her test yönteminin başlangıcında kodu çalıştıran bir `[TestInitialize]` özniteliğiyle tanımlanan bir test Initialize yöntemi ekleyin. Örneğin, uygulamayı TestInitialize yönteminden başlatabilirsiniz.

- Her test yönteminin sonunda kodu çalıştıran bir `[TestCleanup]` özniteliğiyle tanımlanan bir test temizleme yöntemi ekleyin. Örneğin, uygulamayı kapatmak için yöntemi TestCleanup yönteminden çağrılabilir.

## <a name="validate-the-properties-of-ui-controls"></a>UI denetimlerinin özelliklerini doğrulama

Test için [UIMap](/previous-versions/dd580454(v=vs.140)) 'e bir kullanıcı ARABIRIMI (UI) denetimi eklemek veya bir UI denetimi için onay kullanan bir doğrulama yöntemi için kod oluşturmak üzere **kodlanmış UI test oluşturucusunu** kullanabilirsiniz.

UI Denetimleriniz için onay oluşturmak için, **KODLANMıŞ UI Test Oluşturucusu** 'Nda **onaylama Ekle** aracını seçin ve test edilen uygulamanın altındaki denetime doğru bir şekilde, doğrulamak istediğiniz denetime sürükleyin. Kutu denetiminizi özetler, fare düğmesini bırakın. Denetim sınıfı kodu, *UIMap.Designer.cs* dosyasında hemen oluşturulur.

![Kodlanmış UI test hedefleme öğesi](../test/media/codedui_1.png)

Bu denetimin özellikleri artık onaylar **Ekle** iletişim kutusunda listelenir.

Belirli bir denetime gitmenin bir diğer yolu da, **Kullanıcı arabirimi denetim eşlemesi**görünümünü genişletmek için oku **(< <)** kullanmaktır. Üst, eşdüzey veya alt denetim bulmak için haritada herhangi bir yere tıklayabilir ve ok tuşlarını kullanarak ağaç etrafında hareket edebilirsiniz.

![Kodlanmış UI testi özellikleri](../test/media/codedui_2.png)

> [!TIP]
> Uygulamanızda bir denetim seçtiğinizde herhangi bir özellik görmüyorsanız veya Kullanıcı arabirimi denetim eşlemesinde denetimi görmüyorsanız, denetimin uygulama kodunda benzersiz bir KIMLIĞE sahip olduğunu doğrulayın. Benzersiz KIMLIK bir HTML ID özniteliği veya WPF UId olabilir.

Daha sonra, doğrulamak istediğiniz UI denetiminin özelliğindeki kısayol menüsünü açın ve **onaylama Ekle**' ye gelin. **Onaylama Ekle** iletişim kutusunda, onayınız için **karşılaştırıcı** ' yı seçin (örneğin <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A>) ve bir **karşılaştırma değerinde**onayınız için değeri yazın.

![Kodlanmış UI testi onayları](../test/media/codedui_3.png)

Testiniz için tüm onaylarınızı eklediğinizde **Tamam**' ı seçin.

Onaylarınız için kod oluşturmak ve Kullanıcı arabirimi eşlemesine denetim eklemek için **kod oluştur** simgesini seçin. Kodlanmış UI Test yönteminiz için bir ad ve yöntem için açıklama olarak eklenecek Yöntem için bir açıklama yazın. **Ekle ve Oluştur '** a tıklayın. Sonra, **KODLANMıŞ UI Test Oluşturucusu**'nu kapatmak için **Kapat** simgesini seçin. Bu, aşağıdaki koda benzer bir kod üretir. Örneğin, girdiğiniz ad `AssertForAddTwoNumbers`, kod şu örneğe benzer şekilde görünür:

- AssertForAddTwoNumbers onaylama yöntemine, kodlanmış UI test dosyanızdaki test yöntemine bir çağrı ekler:

    ```csharp
    [TestMethod]
    public void CodedUITestMethod1()
    {
        this.UIMap.AddTwoNumbers();
        this.UIMap.AssertForAddTwoNumbers();
    }
    ```

     Adımların ve onayların sırasını değiştirmek veya yeni test yöntemleri oluşturmak için bu dosyayı düzenleyebilirsiniz. Daha fazla kod eklemek için, imleci test yöntemine yerleştirin ve kısayol menüsünde, **KODLANMıŞ UI testi Için kod oluştur**' u seçin.

- UI haritanızda `AssertForAddTwoNumbers` adlı bir yöntem ekler (*UIMap. UITest*). Bu dosya, onayları düzenleyebileceğiniz, **KODLANMıŞ UI Test Düzenleyicisi**'nde açılır.

     ![Kodlanmış UI test düzenleyicisini kullanarak onayı düzenleme](../test/media/cuit_editor_assert.png)

     Daha fazla bilgi için bkz. [kodlanmış UI test düzenleyicisini kullanarak KODLANMıŞ UI testlerini düzenleme](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).

     Ayrıca, *UIMap.Designer.cs*içinde onay yönteminin oluşturulan kodunu görüntüleyebilirsiniz. Ancak, bu dosyayı düzenlememelisiniz. Kodun uyarlanan bir sürümünü yapmak istiyorsanız, yöntemleri *UIMap.cs*gibi başka bir dosyaya kopyalayın, yöntemleri yeniden adlandırın ve orada düzenleyin.

    ```csharp
    public void AssertForAddTwoNumbers()
    {
        ...
    }
    ```

### <a name="select-a-hidden-control-using-the-keyboard"></a>Klavyeyi kullanarak gizli bir denetim seçme

Seçmek istediğiniz denetim odağı kaybeder ve **KODLANMıŞ UI Test Oluşturucusu**'Ndan **onaylama Ekle** aracını seçtiğinizde kaybolur:

Bazen, denetimler eklediğinizde ve özelliklerini doğruladıktan sonra klavyeyi kullanmanız gerekebilir. Örneğin, sağ tıklama menü denetimini kullanan bir kodlanmış UI testini kaydetmeye çalıştığınızda, denetimdeki menü öğelerinin listesi odağı kaybeder ve **KODLANMıŞ UI Test Oluşturucusu**'Ndan onay **Ekle** aracını seçmeyi denediğinizde kaybolur. Bu, Internet Explorer 'daki sağ tıklama menüsünün odağı kaybetmesi ve onay **Ekle** aracı ile seçmeyi denerseniz kaybolur, aşağıdaki çizimde gösterilmiştir.

![CodedUITest&#95;selectcontrolkeyboard](../test/media/codeduitest_selectcontrolkeyboard.png)

Bir UI denetimi seçmek üzere klavyeyi kullanmak için fare ile denetimin üzerine gelin. Ardından **CTRL** tuşunu ve **ı** tuşunu aynı anda basılı tutun. Anahtarları serbest bırakın. Denetim, **KODLANMıŞ UI Test Oluşturucusu**tarafından kaydedilir.

#### <a name="manually-record-mouse-hovers"></a>Fareyi el ile kaydet

Bir denetimin üzerine bir fare ile yer kaydıysanız:

Bazı durumlarda, kodlanmış UI testinde kullanılan belirli bir denetim, fare üzerine gelme olaylarını el ile kaydetmek için klavyeyi kullanmanızı gerektirebilir. Örneğin, bir Windows formunu veya Windows Presentation Foundation (WPF) uygulamasını test ettiğinizde özel kod olabilir. Ya da, bir denetimin üzerine gelindiğinde, bir kullanıcı onun üzerine geldiğinde genişleyen bir ağaç düğümü gibi özel davranışlar tanımlanmış olabilir. Bunlar gibi durumları test etmek için, önceden tanımlanmış klavye tuşlarına basarak, denetimin üzerine geldiğinizde **KODLANMıŞ UI Test Oluşturucusu** 'nu el ile bilgilendirmeniz gerekir.

Kodlanmış UI testinizi gerçekleştirdiğinizde, denetimin üzerine gelin. Ardından, klavyenizde **Shift** ve **R** tuşlarını basılı tutarken **CTRL**tuşunu basılı tutun. Anahtarları serbest bırakın. Bir fare üzerine gelme olayı, **KODLANMıŞ UI Test Oluşturucusu**tarafından kaydedilir.

![CodedUI&#95;üzerine gelme](../test/media/codedui_hover.png)

Test yöntemini oluşturduktan sonra, aşağıdaki örneğe benzer bir kod *UIMap.Designer.cs* dosyasına eklenecektir:

```csharp
// Mouse hover '1' label at (87, 9)
Mouse.Hover(uIItem1Text, new Point(87, 9));
```

### <a name="configure-mouse-hover-keyboard-assignments"></a>Fareyle üzerine gelme klavye atamalarını yapılandırma

Fare üzerine gelme olaylarını yakalamaya yönelik anahtar ataması ortammda başka bir yerde kullanılıyorsa:

Gerekirse, kodlanmış UI testlerinizde fare üzerine gelme olaylarını uygulamak için kullanılan **Ctrl** +**SHIFT** +**R** 'nin varsayılan klavye ataması farklı anahtarlar kullanacak şekilde yapılandırılabilir.

> [!WARNING]
> Normal koşullarda fare üzerine gelme olayları için klavye atamalarını değiştirmeniz gerekmez. Klavye atamasını yeniden atayarak dikkatli olun. Seçiminiz, Visual Studio içinde başka bir yerde veya test edilmekte olan uygulamanın zaten kullanılıyor olabilir.

Klavye atamalarını değiştirmek için aşağıdaki yapılandırma dosyasını değiştirin:

*% ProgramFiles (x86)% \ Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CodedUITestBuilder.exe.config*

Yapılandırma dosyasında, klavye atamalarını değiştirmek için `HoverKeyModifier` ve `HoverKey` anahtarlarının değerlerini değiştirin:

```xml
<!-- Begin : Background Recorder Settings -->
<!-- HoverKey to use. -->
<add key="HoverKeyModifier" value="Control, Shift"/>
<add key="HoverKey" value="R"/>
```

### <a name="set-implicit-mouse-hovers-for-the-web-browser"></a>Web tarayıcısı için örtülü fare imlecini ayarla

Sorun yaşıyorsanız fare bir Web sitesinde dolaştığında:

Birçok Web sitesinde, belirli bir denetimin üzerine geldiğinizde, ek ayrıntıları göstermek için genişler. Genellikle bu, masaüstü uygulamalarında menüler gibi görünür. Bu ortak bir model olduğundan, kodlanmış UI testleri Web 'e göz atmaya yönelik örtülü olarak dolaşmasını etkinleştirir. Örneğin, Internet Explorer 'da geldiğinde kayıt yaparsanız bir olay tetiklenir. Bu olaylar, kaydedilen sonuçlara yol açabilir. Bu nedenle, örtük olarak, Kullanıcı arabirimi test yapılandırma dosyasında `true` olarak ayarlanmış `ContinueOnError` kaydedilir. Bu, bir vurgulama olayı başarısız olursa kayıttan yürütmenin devam etmesine olanak tanır.

Bir Web tarayıcısında örtük olarak bekletilme kaydını etkinleştirmek için yapılandırma dosyasını açın:

*% ProgramFiles (x86)% \ Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CodedUITestBuilder.exe.config*

Aşağıdaki örnekte gösterildiği gibi, yapılandırma dosyasının anahtar `RecordImplicitiHovers` bir `true` değerine ayarlandığını doğrulayın:

```xml
<!--Use this to enable/disable recording of implicit hovers.-->
<add key="RecordImplicitHover" value="true"/>
```

## <a name="customize-the-coded-ui-test"></a>Kodlanmış UI testini özelleştirme

Kodlanmış UI testinizi oluşturduktan sonra, Visual Studio 'da aşağıdaki araçlardan herhangi birini kullanarak düzenleyebilirsiniz:

- Testlerinize ek denetimler ve doğrulama eklemek için **KODLANMıŞ UI test oluşturucusunu** kullanın. Bu konudaki [denetim ekleme ve özelliklerini doğrulama](#validate-the-properties-of-ui-controls) bölümüne bakın.

- **KODLANMıŞ UI Testi Düzenleyicisi** , kodlanmış UI testlerinizi kolayca değiştirmenize olanak sağlar. **KODLANMıŞ UI test düzenleyicisini**kullanarak test yöntemlerinizi bulabilir, görüntüleyebilir ve düzenleyebilirsiniz. UI eylemlerini ve bunlarla ilişkili denetimleri kullanıcı arabirimi denetim eşlemesinde da düzenleyebilirsiniz. Daha fazla bilgi için bkz. [kodlanmış UI test düzenleyicisini kullanarak KODLANMıŞ UI testlerini düzenleme](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).

- **Kod Düzenleyicisi:**

  - Bu konunun [KODLANMıŞ UI Denetim eylemleri ve özellikleri](#coded-ui-control-actions-and-properties) bölümünde açıklandığı gibi, testinizde denetimler için kod el ile ekleyin.

  - Kodlanmış UI testi oluşturduktan sonra, bunu veri odaklı olacak şekilde değiştirebilirsiniz. Daha fazla bilgi için bkz. [veri odaklı KODLANMıŞ UI testi oluşturma](../test/creating-a-data-driven-coded-ui-test.md).

  - Kodlanmış bir UI Testi Kayıttan yürütmede, teste bir pencere, ilerleme çubuğunun kaybolması gibi belirli olayların gerçekleşmesini beklemek için teste talimat verebilirsiniz. Bunu yapmak için, uygun UITestControl. WaitForControlXXX () metodunu ekleyin. Kullanılabilir yöntemlerin tüm listesi için bkz. [kayıttan yürütme sırasında KODLANMıŞ UI testlerinin belirli olayları beklemesini sağlama](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md). WaitForControlEnabled yöntemi kullanılarak bir denetimin etkinleştirilmesini bekleyen kodlanmış UI testinin bir örneği için bkz. [Izlenecek yol: kodlanmış BIR UI testi oluşturma, düzenlemeyle ve sürdürme](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md).

  - Kodlanmış UI testleri, Internet Explorer 9 ve Internet Explorer 10 ' da bulunan HTML5 denetimlerinin bazılarına yönelik destek içerir. Daha fazla bilgi için bkz. [KODLANMıŞ UI TESTLERINDE HTML5 denetimleri kullanma](../test/using-html5-controls-in-coded-ui-tests.md).

  - Kodlanmış UI test kodlama Kılavuzu:

    - [Kodlanmış UI testinin anatomumu](../test/anatomy-of-a-coded-ui-test.md)

    - [Kodlanmış UI testleri için en iyi uygulamalar](../test/best-practices-for-coded-ui-tests.md)

    - [Birden çok UI haritası ile büyük bir uygulamayı test etme](../test/testing-a-large-application-with-multiple-ui-maps.md)

    - [Kodlanmış UI testleri ve eylem kayıtları için desteklenen konfigürasyonlar ve platformlar](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)

### <a name="the-generated-code"></a>Oluşturulan kod

**Kod oluştur**' u seçtiğinizde, çeşitli kod parçaları oluşturulur:

- Test yönteminde bir çizgi.

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

     Daha fazla kayıtlı eylem ve doğrulama eklemek için bu yöntemde sağ tıklayabilirsiniz. Ayrıca, kodu genişletmek veya değiştirmek için el ile de düzenleyebilirsiniz. Örneğin, bazı kodları bir döngüde alabilirsiniz.

     Ayrıca, yeni test yöntemleri ekleyebilir ve bunlara aynı şekilde kod ekleyebilirsiniz. Her test yönteminin `[TestMethod]` özniteliği olmalıdır.

- *UIMap. UITest*içindeki bir yöntem.

     Bu yöntem, kaydettiğiniz eylemlerin veya doğrulamış olduğunuz değerin ayrıntılarını içerir. *UIMap. UITest*' i açarak bu kodu düzenleyebilirsiniz. Kayıtlı eylemleri silebilmeniz veya yeniden düzenleyebileceğiniz özelleştirilmiş bir düzenleyicide açılır.

     Ayrıca, *UIMap.Designer.cs*içinde oluşturulan yöntemi görüntüleyebilirsiniz. Bu yöntem, testi çalıştırdığınızda kaydettiğiniz eylemleri gerçekleştirir.

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
    > Daha fazla test oluşturduğunuzda yeniden üretilecek olduğundan, bu dosyayı düzenlememelisiniz.

     Bu yöntemlerin uyarlanan sürümlerini *UIMap.cs*'e kopyalayarak yapabilirsiniz. Örneğin, bir test yönteminden çağırabilmeniz için parametreli bir sürüm yapabilirsiniz:

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

- *UIMap. UITest*içindeki bildirimler.

    Bu bildirimler, testinizin kullandığı uygulamanın kullanıcı arabirimi denetimlerini temsil eder. Bunlar, denetimleri çalıştırmak ve özelliklerine erişmek için oluşturulan kod tarafından kullanılır.

    Ayrıca, kendi kodunuzu yazarsanız de kullanabilirsiniz. Örneğin, test yönteminizin bir Web uygulamasında köprü seçmesini, bir metin kutusuna bir değer yazmasını veya bir alandaki bir değere göre farklı test eylemleri ele geçirmesine sahip olabilirsiniz.

    Büyük bir uygulamanın test edilmesini kolaylaştırmak için birden çok kodlanmış UI testi ve birden çok UI eşlemesi nesnesi ve dosyası ekleyebilirsiniz. Daha fazla bilgi için bkz. [birden çok UI haritası ile büyük bir uygulamayı test](../test/testing-a-large-application-with-multiple-ui-maps.md)etme.

Oluşturulan kod hakkında daha fazla bilgi için bkz. [KODLANMıŞ UI testinin Anatomy](../test/anatomy-of-a-coded-ui-test.md).

## <a name="coded-ui-control-actions-and-properties"></a>Kodlanmış UI Denetim eylemleri ve özellikleri

Kodlanmış UI testlerinde UI test denetimleriyle çalışırken, bunlar iki bölümden ayrılır: eylemler ve Özellikler.

- İlk bölüm, UI test denetimlerinde gerçekleştirebileceğiniz eylemlerden oluşur. Örneğin, kodlanmış UI testleri bir UI test denetiminde fare tıklamalarını taklit edebilir veya bir UI test denetimini etkilemek için klavyede yazılan anahtarların benzetimini yapabilir.

- İkinci bölüm, bir UI test denetiminde özellikleri almanıza ve ayarlamanıza olanak tanıyarak oluşur. Örneğin, kodlanmış UI testleri bir `ListBox` öğelerin sayısını alabilir veya seçili duruma bir `CheckBox` ayarlayabilir.

**UI test denetimindeki eylemlere erişme**

Kullanıcı arabirimi test denetimleri üzerinde fare tıklamaları veya klavye eylemleri gibi eylemler gerçekleştirmek için <xref:Microsoft.VisualStudio.TestTools.UITesting.Mouse> ve <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard> sınıflarında yöntemleri kullanın:

- Bir kullanıcı arabirimi test denetiminde fare tıklaması gibi fare yönelimli bir eylem gerçekleştirmek için <xref:Microsoft.VisualStudio.TestTools.UITesting.Mouse.Click%2A> kullanın.

     `Mouse.Click(buttonCancel);`

- Bir düzenleme denetimine yazma gibi klavye odaklı bir eylem gerçekleştirmek için <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard.SendKeys%2A> kullanın.

     `Keyboard.SendKeys(textBoxDestination, @"C:\Temp\Output.txt");`

**UI test denetiminin özelliklerine erişme**

UI denetimine özgü özellik değerlerini almak ve ayarlamak için, bir denetimin özelliklerinin değerlerini doğrudan alabilir veya ayarlayabilirsiniz veya <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A?displayProperty=fullName> ve <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A?displayProperty=fullName> yöntemlerini, almak veya ayarlamak istediğiniz belirli özelliğin adıyla birlikte kullanabilirsiniz.

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A>, daha sonra uygun <xref:System.Type> cast olabilecek bir nesne döndürür. <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A>, özelliğin değeri için bir nesne kabul eder.

### <a name="to-get-or-set-properties-from-ui-test-controls-directly"></a>UI test denetimlerinden doğrudan özellik almak veya ayarlamak için

[HtmlList](xref:Microsoft.VisualStudio.TestTools.UITesting.HtmlControls.HtmlList) veya [wincombobox](xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls.WinComboBox)gibi <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl> türetilen denetimlerle, özellik değerlerini doğrudan alabilir veya ayarlayabilirsiniz. Aşağıdaki kod bazı örnekleri göstermektedir:

```csharp
int i = myHtmlList.ItemCount;
myWinCheckBox.Checked = true;
```

### <a name="to-get-properties-from-ui-test-controls"></a>UI test denetimlerinden özellikleri almak için

- Bir denetimden Özellik değeri almak için <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A> kullanın.

- Alınacak denetimin özelliğini belirtmek için, <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A> parametresi olarak her denetimdeki `PropertyNames` sınıftan uygun dizeyi kullanın.

- <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A> uygun veri türünü döndürür, ancak bu dönüş değeri bir <xref:System.Object> olarak dönüştürüldü. Dönüş <xref:System.Object> uygun tür olarak yayınlanmalıdır.

     Örnek:

     `int i = (int)GetProperty(myHtmlList.PropertyNames.ItemCount);`

### <a name="to-set-properties-for-ui-test-controls"></a>UI test denetimleri için özellikleri ayarlamak için

- Bir denetimdeki özelliği ayarlamak için <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A> kullanın.

- Ayarlanacak denetimin özelliğini belirtmek için, ikinci parametre olarak özellik değeri ile, `PropertyNames` sınıfından <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A> ilk parametre olarak uygun dizeyi kullanın.

     Örnek:

     `SetProperty(myWinCheckBox.PropertyNames.Checked, true);`

## <a name="debug"></a>Hata ayıklama

Kodlanmış UI test günlüklerini kullanarak kodlanmış UI testlerini çözümleyebilirsiniz. Kodlanmış UI test günlükleri, kodlanmış UI test çalışmalarınız hakkında önemli bilgileri filtreleyip kaydeder. Günlüklerin biçimi sorunları hızlı bir şekilde ayıklamanıza olanak tanır. Daha fazla bilgi için bkz. [KODLANMıŞ UI test günlüklerini kullanarak KODLANMıŞ UI testlerini çözümleme](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md).

## <a name="whats-next"></a>Sırada ne var?

**KODLANMıŞ UI testlerini çalıştırmak Için ek seçenekler:** Kodlanmış UI testlerini, bu konuda daha önce açıklandığı gibi doğrudan Visual Studio 'dan çalıştırabilirsiniz. Ayrıca, Microsoft Test Yöneticisi veya Azure Pipelines kullanarak otomatikleştirilmiş UI testleri çalıştırabilirsiniz. Kodlanmış UI testleri otomatikleştirildiğinde, diğer otomatikleştirilmiş testlerin aksine, bunları çalıştırdığınızda masaüstüyle etkileşim kurması gerekir.

- [Test Gezgini ile birim testleri çalıştırma](../test/run-unit-tests-with-test-explorer.md)

- [Yapı sürecinizdeki testleri çalıştırın](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts)

- [Nasıl yapılır: Masaüstü ile etkileşimi olan testleri çalıştırmak için test aracınızı ayarlama](https://msdn.microsoft.com/Library/3a94dd07-6d17-402c-ae8f-7947143755c9)

**Özel denetimler için destek ekleme:**  Kodlanmış UI test çerçevesi olası her kullanıcı arabirimini desteklemez ve test etmek istediğiniz kullanıcı arabirimini desteklemeyebilir. Örneğin, Microsoft Excel için Kullanıcı arabiriminin kodlanmış UI testini hemen oluşturamazsınız. Ancak, özel bir denetimi destekleyen kodlanmış UI testi çerçevesine bir uzantı oluşturabilirsiniz.

- [Denetimlerinizin kodlanmış UI testlerini etkinleştirme](../test/enable-coded-ui-testing-of-your-controls.md)

- [Kodlanmış UI testlerini ve eylem kayıtlarını genişletme](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)

Kodlanmış UI testleri, genellikle el ile testleri otomatikleştirmek için kullanılır. El ile testler hakkında daha fazla bilgi için bkz. [Microsoft Test Yöneticisi ile el ile testleri çalıştırma](/azure/devops/test/mtm/run-manual-tests-with-microsoft-test-manager?view=vsts). Otomatikleştirilmiş testler hakkında daha fazla bilgi için bkz. [Visual Studio 'Da test araçları](../test/improve-code-quality.md).

## <a name="see-also"></a>Ayrıca bkz.

- [El ile testleri kaydetme ve kayıttan yürütme](/azure/devops/test/mtm/record-play-back-manual-tests?view=vsts)
- [Xamarin. UITest](/appcenter/test-cloud/uitest/)
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>
- [İzlenecek yol: kodlanmış bir UI testi oluşturma, düzenleme ve sürdürme](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
- [UWP uygulamasını test etmek için kodlanmış UI testi oluşturma](test-uwp-app-with-coded-ui-test.md)
- [Kodlanmış UI testinin anatomumu](../test/anatomy-of-a-coded-ui-test.md)
- [Kodlanmış UI testleri için en iyi uygulamalar](../test/best-practices-for-coded-ui-tests.md)
- [Birden çok UI haritası ile büyük bir uygulamayı test etme](../test/testing-a-large-application-with-multiple-ui-maps.md)
