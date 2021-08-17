---
title: Kodlanmış UI testleri
description: kodlanmış uı testi oluşturucusu arka planda çalışırken el ile testi gerçekleştirerek Visual Studio kodlanmış bir uı testinin nasıl oluşturulacağını öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
ms.openlocfilehash: 2422261a8eea07eff963d9bf94fa9db26ba7415618b7bdc2cac9b9e80f130298
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121424979"
---
# <a name="use-coded-ui-test-to-test-your-code"></a>Kodunuzu test etmek için kodlanmış UI testi kullanın

Kodlanmış UI testleri (CUITs) uygulamanızın kullanıcı arabirimi (UI) aracılığıyla sürüşü. Bu sınamalar, UI denetimlerinin işlevsel sınamasını içerir. Bu kişiler, Kullanıcı arabirimi de dahil olmak üzere tüm uygulamanın doğru şekilde çalıştığını doğrulamanızı sağlar. Kodlanmış UI testleri, Kullanıcı arabiriminde, örneğin bir Web sayfasında doğrulama veya başka bir mantık olduğunda faydalıdır. Ayrıca, var olan bir el ile testi otomatikleştirmek için sık kullanılır.

Visual Studio bir kodlanmış uı testinin oluşturulması kolaydır. **KODLANMıŞ UI Test Oluşturucusu** arka planda çalışırken testi yalnızca el ile gerçekleştirirsiniz. Ayrıca, belirli alanlarda görüntülenecek değerleri de belirtebilirsiniz. **KODLANMıŞ UI Test Oluşturucusu** eylemlerinizi kaydeder ve bunlardan kod oluşturur. Test oluşturulduktan sonra, eylem dizisini değiştirmenize olanak sağlayan özelleştirilmiş bir düzenleyicide düzenleyebilirsiniz.

Özelleştirilmiş **KODLANMıŞ UI Test Oluşturucusu** ve düzenleyici, kodlanmış UI testlerini oluşturmayı ve düzenlemenizi kolaylaştırır, bu da ana becerilerinizi kodlama yerine test halinde yoğunlaşdı. Ancak bir geliştiricisiyseniz ve testi daha gelişmiş bir şekilde genişletmek istiyorsanız, kod yapılandırılmıştır ve uyarlanabilmesi için yapılandırılır. Örneğin, bir Web sitesinde bir şey satın almak için bir test kaydedebilir ve sonra çok sayıda öğe alan bir döngü eklemek için oluşturulan kodu düzenleyebilirsiniz.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="requirements"></a>Gereksinimler

- Visual Studio Enterprise
- Kodlanmış UI test bileşeni

Kodlanmış UI testleri tarafından desteklenen platformlar ve Konfigürasyonlar hakkında daha fazla bilgi için bkz. [Desteklenen platformlar](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md).

## <a name="install-the-coded-ui-test-component"></a>Kodlanmış UI test bileşenini yükler

Kodlanmış UI test araçlarına ve şablonlarına erişmek için, Visual Studio **KODLANMıŞ UI test** bileşenini yükler.

1. araçlar    >  **ve özellikler al ' i** seçerek Visual Studio Yükleyicisi başlatın.

1. **Visual Studio Yükleyicisi**, **tek tek bileşenler** sekmesini seçin ve ardından aşağı kaydırarak **hata ayıklama ve test** bölümüne gidin. **KODLANMıŞ UI test** bileşeni seçin.

   ![Kodlanmış UI test bileşeni](media/coded-ui-test-component.png)

1. **Değiştir**'i seçin.

## <a name="create-a-coded-ui-test"></a>Kodlanmış UI testi oluşturma

1. Kodlanmış UI test projesi oluşturun.

   Kodlanmış UI testleri kodlanmış UI testi projesinde bulunmalıdır. Zaten kodlanmış bir UI test projeniz yoksa, bir tane oluşturun. **dosya**  >  **yeni**  >  **Project** seçin. **kodlanmış uı testi Project** proje şablonunu arayın ve seçin.

   ::: moniker range="vs-2017"

   ![yeni Project iletişim kutusunda kodlanmış uı test projesi şablonu](media/coded-ui-test-project-template.png)

   ::: moniker-end

   > [!NOTE]
   > **kodlanmış uı testi Project** şablonu görmüyorsanız, [kodlanmış uı test bileşenini yüklemeniz](../test/use-ui-automation-to-test-your-code.md#install-the-coded-ui-test-component)gerekir.

2. Kodlanmış UI test dosyası ekleyin.

     Yalnızca kodlanmış bir UI projesi oluşturduysanız, ilk CUIT dosyası otomatik olarak eklenir. Başka bir test dosyası eklemek için, **Çözüm Gezgini**' de kodlanmış UI testi projesinde kısayol menüsünü açın ve sonra   >  **kodlanmış UI testi** Ekle ' yi seçin.

     **Kodlanmış UI testi için kod üret** iletişim kutusunda, **kayıt eylemleri**  >  **Kullanıcı Arabirimi eşlemesini Düzenle veya onaylama Ekle** seçeneklerini belirleyin.

     ![Kodlanmış UI testi iletişim kutusu için kod oluştur](media/generate-code-for-coded-ui-test.png)

     **KODLANMıŞ UI Test Oluşturucusu** görüntülenir.

     ![Kodlanmış UI Test Oluşturucusu](../test/media/codedui_testbuilder.png)

3. Bir dizi eylemi kaydedin.

     **Kaydı başlatmak Için** **kayıt** simgesini seçin. Uygulamanızda test etmek istediğiniz eylemleri, bu gerekliyse uygulamayı başlatma dahil olmak üzere gerçekleştirin. Örneğin, bir Web uygulamasını test ediyorsanız, bir tarayıcı başlatabilir, Web sitesine gidebilir ve uygulamada oturum açmanız gerekebilir.

     **Kaydı duraklatmak için** Örneğin, gelen posta ile uğraşmanız gerekiyorsa, **Duraklat**' ı seçin.

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

     *UIMap. UITest* öğesini açın. Bu dosya, **KODLANMıŞ UI Test Düzenleyicisi**'nde açılır. burada, kaydettiğiniz herhangi bir işlem dizisini düzenleyebilir ve onaylarınızı düzenleyebilirsiniz.

     ![Kodlanmış UI Test Düzenleyicisi](../test/media/cuit_editor_edit.png)

     Daha fazla bilgi için bkz. [kodlanmış UI test düzenleyicisini kullanarak KODLANMıŞ UI testlerini düzenleme](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).

8. Testi çalıştırın.

   Test Gezgini 'ni kullanın veya test yönteminde kısayol menüsünü açın ve **Testleri Çalıştır**' ı seçin. Testlerin nasıl çalıştırılacağı hakkında daha fazla bilgi için, bkz. [Test Gezgini ile birim testlerini çalıştırma](../test/run-unit-tests-with-test-explorer.md) ve bu konunun sonundaki [sonraki nedir?](#whats-next) bölümünde *kodlanmış UI testlerini çalıştırmak için ek seçenekler* .

Bu konudaki geri kalan bölümler, bu yordamdaki adımlar hakkında daha fazla ayrıntı sağlar.

Daha ayrıntılı bir örnek için bkz. [Izlenecek yol: kodlanmış BIR UI testi oluşturma, düzenlemeyle ve sürdürme](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md). izlenecek yolda, kodlanmış uı testinin nasıl oluşturulduğunu, düzenleneceğini ve bakımının nasıl yapılacağını göstermek için basit bir Windows Presentation Foundation (WPF) uygulaması oluşturacaksınız. İzlenecek yol çeşitli zamanlama sorunları ve yeniden düzenlemeyi denetleme tarafından kırılan testleri düzeltmeye ilişkin çözümler sağlar.

## <a name="start-and-stop-the-application-under-test"></a>Test edilen uygulamayı başlatma ve durdurma

Her test için uygulama, tarayıcı veya veritabanını ayrı olarak başlatıp durdurmak istemiyorsanız, aşağıdakilerden birini yapın:

- Uygulamanızı test altına başlatmak üzere eylemleri kaydetmek istemiyorsanız, **kayıt** simgesini seçmeden önce uygulamanızı başlatmanız gerekir.

- Testin sonunda, testin çalıştırıldığı işlem sonlandırılır. Uygulamanızı testte başlattıysanız uygulama genellikle kapanır.  Testin, çıkış sırasında uygulamanızı kapatmasını istemiyorsanız, çözümünüze bir *. runsettings* dosyası ekleyin ve `KeepExecutorAliveAfterLegacyRun` seçeneğini kullanın. Daha fazla bilgi için bkz [.. runsettings dosyasını kullanarak birim testlerini yapılandırma](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).

- `[TestInitialize]`Her test yönteminin başlangıcında kodu çalıştıran bir özniteliğiyle tanımlanan bir test Initialize yöntemi ekleyin. Örneğin, uygulamayı TestInitialize yönteminden başlatabilirsiniz.

- `[TestCleanup]`Her test yönteminin sonunda kodu çalıştıran bir özniteliği tarafından tanımlanan bir test temizleme yöntemi ekleyin. Örneğin, uygulamayı kapatmak için yöntemi TestCleanup yönteminden çağrılabilir.

## <a name="validate-the-properties-of-ui-controls"></a>UI denetimlerinin özelliklerini doğrulama

Test için [UIMap](/previous-versions/dd580454(v=vs.140)) 'e bir kullanıcı ARABIRIMI (UI) denetimi eklemek veya bir UI denetimi için onay kullanan bir doğrulama yöntemi için kod oluşturmak üzere **kodlanmış UI test oluşturucusunu** kullanabilirsiniz.

UI Denetimleriniz için onay oluşturmak için, **KODLANMıŞ UI Test Oluşturucusu** 'Nda **onaylama Ekle** aracını seçin ve test edilen uygulamanın altındaki denetime doğru bir şekilde, doğrulamak istediğiniz denetime sürükleyin. Kutu denetiminizi özetler, fare düğmesini bırakın. Denetim sınıfı kodu, *UIMap. Designer. cs* dosyasında hemen oluşturulur.

![Kodlanmış UI test hedefleme öğesi](../test/media/codedui_1.png)

Bu denetimin özellikleri artık onaylar **Ekle** iletişim kutusunda listelenir.

Belirli bir denetime gitmenin bir diğer yolu da, **Kullanıcı arabirimi denetim eşlemesi** için görünümü genişletmek üzere ok **(<<)** seçeneğini kullanmaktır. Üst, eşdüzey veya alt denetim bulmak için haritada herhangi bir yere tıklayabilir ve ok tuşlarını kullanarak ağaç etrafında hareket edebilirsiniz.

![Kodlanmış UI testi özellikleri](../test/media/codedui_2.png)

> [!TIP]
> Uygulamanızda bir denetim seçtiğinizde herhangi bir özellik görmüyorsanız veya Kullanıcı arabirimi denetim eşlemesinde denetimi görmüyorsanız, denetimin uygulama kodunda benzersiz bir KIMLIĞE sahip olduğunu doğrulayın. Benzersiz KIMLIK bir HTML ID özniteliği veya WPF UId olabilir.

Daha sonra, doğrulamak istediğiniz UI denetiminin özelliğindeki kısayol menüsünü açın ve **onaylama Ekle**' ye gelin. **Onaylama Ekle** iletişim kutusunda, onayınız için **karşılaştırıcı** ' yı seçin, örneğin <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A> , **karşılaştırma değeri**' nde onayınız için değer yazın.

![Kodlanmış UI testi onayları](../test/media/codedui_3.png)

Testiniz için tüm onaylarınızı eklediğinizde **Tamam**' ı seçin.

Onaylarınız için kod oluşturmak ve Kullanıcı arabirimi eşlemesine denetim eklemek için **kod oluştur** simgesini seçin. Kodlanmış UI Test yönteminiz için bir ad ve yöntem için açıklama olarak eklenecek Yöntem için bir açıklama yazın. **Ekle ve Oluştur '** a tıklayın. Sonra, **KODLANMıŞ UI Test Oluşturucusu**'nu kapatmak için **Kapat** simgesini seçin. Bu, aşağıdaki koda benzer bir kod üretir. Örneğin, girdiğiniz ad ise `AssertForAddTwoNumbers` , kod şu örneğe benzer şekilde görünür:

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

- `AssertForAddTwoNumbers`UI haritanızda (*UIMap. UITest*) adlı bir yöntem ekler. Bu dosya, onayları düzenleyebileceğiniz, **KODLANMıŞ UI Test Düzenleyicisi**'nde açılır.

     ![Kodlanmış UI test düzenleyicisini kullanarak onayı düzenleme](../test/media/cuit_editor_assert.png)

     Daha fazla bilgi için bkz. [kodlanmış UI test düzenleyicisini kullanarak KODLANMıŞ UI testlerini düzenleme](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).

     Ayrıca, *UIMap. Designer. cs* dosyasındaki onaylama yönteminin oluşturulan kodunu görüntüleyebilirsiniz. Ancak, bu dosyayı düzenlememelisiniz. Kodun uyarlanan bir sürümünü yapmak istiyorsanız, yöntemleri *UIMap. cs* gibi başka bir dosyaya kopyalayın, yöntemleri yeniden adlandırın ve orada düzenleyin.

    ```csharp
    public void AssertForAddTwoNumbers()
    {
        ...
    }
    ```

### <a name="select-a-hidden-control-using-the-keyboard"></a>Klavyeyi kullanarak gizli bir denetim seçme

Seçmek istediğiniz denetim odağı kaybeder ve **KODLANMıŞ UI Test Oluşturucusu**'Ndan **onaylama Ekle** aracını seçtiğinizde kaybolur:

Bazen, denetimler eklediğinizde ve özelliklerini doğruladıktan sonra klavyeyi kullanmanız gerekebilir. Örneğin, sağ tıklama menü denetimini kullanan bir kodlanmış UI testini kaydetmeye çalıştığınızda, denetimdeki menü öğelerinin listesi odağı kaybeder ve **KODLANMıŞ UI Test Oluşturucusu**'Ndan onay **Ekle** aracını seçmeyi denediğinizde kaybolur. Bu, Internet Explorer 'daki sağ tıklama menüsünün odağı kaybetmesi ve onay **Ekle** aracı ile seçmeyi denerseniz kaybolur, aşağıdaki çizimde gösterilmiştir.

![Kodlanmış UI Test Oluşturucusu 'nda, Internet Explorer 'ın sağ tıklama menüsünden çakışan onaylama Ekle aracını gösteren ekran görüntüsü.](../test/media/codeduitest_selectcontrolkeyboard.png)

Bir UI denetimi seçmek üzere klavyeyi kullanmak için fare ile denetimin üzerine gelin. Ardından **CTRL** tuşunu ve **ı** tuşunu aynı anda basılı tutun. Anahtarları serbest bırakın. Denetim, **KODLANMıŞ UI Test Oluşturucusu** tarafından kaydedilir.

#### <a name="manually-record-mouse-hovers"></a>Fareyi el ile kaydet

Bir denetimin üzerine bir fare ile yer kaydıysanız:

Bazı durumlarda, kodlanmış UI testinde kullanılan belirli bir denetim, fare üzerine gelme olaylarını el ile kaydetmek için klavyeyi kullanmanızı gerektirebilir. örneğin, bir Windows formunu veya bir Windows Presentation Foundation (WPF) uygulamasını test ettiğinizde özel kod olabilir. Ya da, bir denetimin üzerine gelindiğinde, bir kullanıcı onun üzerine geldiğinde genişleyen bir ağaç düğümü gibi özel davranışlar tanımlanmış olabilir. Bunlar gibi durumları test etmek için, önceden tanımlanmış klavye tuşlarına basarak, denetimin üzerine geldiğinizde **KODLANMıŞ UI Test Oluşturucusu** 'nu el ile bilgilendirmeniz gerekir.

Kodlanmış UI testinizi gerçekleştirdiğinizde, denetimin üzerine gelin. Ardından, klavyenizde **Shift** ve **R** tuşlarını basılı tutarken **CTRL** tuşunu basılı tutun. Anahtarları serbest bırakın. Bir fare üzerine gelme olayı, **KODLANMıŞ UI Test Oluşturucusu** tarafından kaydedilir.

![Kodlanmış UI Test Oluşturucusu komut çubuğunun duraklatma simgesi seçiliyken ekran görüntüsü. Bir araç ipucu penceresi, fare üzerine gelme olayının konumunu gösterir.](../test/media/codedui_hover.png)

Test yöntemini oluşturduktan sonra, aşağıdaki örneğe benzer bir kod *UIMap. Designer. cs* dosyasına eklenecektir:

```csharp
// Mouse hover '1' label at (87, 9)
Mouse.Hover(uIItem1Text, new Point(87, 9));
```

### <a name="configure-mouse-hover-keyboard-assignments"></a>Fareyle üzerine gelme klavye atamalarını yapılandırma

Fare üzerine gelme olaylarını yakalamaya yönelik anahtar ataması ortammda başka bir yerde kullanılıyorsa:

Gerekirse,  +  + kodlanmış UI testlerinizde fare üzerine gelme olaylarını uygulamak için kullanılan CTRL SHIFT **R** 'nin varsayılan klavye ataması farklı anahtarlar kullanacak şekilde yapılandırılabilir.

> [!WARNING]
> Normal koşullarda fare üzerine gelme olayları için klavye atamalarını değiştirmeniz gerekmez. Klavye atamasını yeniden atayarak dikkatli olun. seçiminiz Visual Studio veya test edilmekte olan uygulama içinde başka bir yerde kullanılıyor olabilir.

Klavye atamalarını değiştirmek için aşağıdaki yapılandırma dosyasını değiştirin:

*% ProgramFiles (x86)% \ Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CodedUITestBuilder.exe.config*

Yapılandırma dosyasında, `HoverKeyModifier` ve anahtarlarının değerlerini değiştirip `HoverKey` klavye atamalarını değiştirin:

```xml
<!-- Begin : Background Recorder Settings -->
<!-- HoverKey to use. -->
<add key="HoverKeyModifier" value="Control, Shift"/>
<add key="HoverKey" value="R"/>
```

### <a name="set-implicit-mouse-hovers-for-the-web-browser"></a>Web tarayıcısı için örtülü fare imlecini ayarla

Sorun yaşıyorsanız fare bir Web sitesinde dolaştığında:

Birçok Web sitesinde, belirli bir denetimin üzerine geldiğinizde, ek ayrıntıları göstermek için genişler. Genellikle bu, masaüstü uygulamalarında menüler gibi görünür. Bu ortak bir model olduğundan, kodlanmış UI testleri Web 'e göz atmaya yönelik örtülü olarak dolaşmasını etkinleştirir. Örneğin, Internet Explorer 'da geldiğinde kayıt yaparsanız bir olay tetiklenir. Bu olaylar, kaydedilen sonuçlara yol açabilir. Bu nedenle, örtük olarak, `ContinueOnError` `true` Kullanıcı arabirimi test yapılandırma dosyasında olarak ayarlanmış olarak kaydedilir. Bu, bir vurgulama olayı başarısız olursa kayıttan yürütmenin devam etmesine olanak tanır.

Bir Web tarayıcısında örtük olarak bekletilme kaydını etkinleştirmek için yapılandırma dosyasını açın:

*% ProgramFiles (x86)% \ Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CodedUITestBuilder.exe.config*

Yapılandırma dosyasının anahtarın `RecordImplicitiHovers` `true` Aşağıdaki örnekte gösterildiği gibi bir değere ayarlandığını doğrulayın:

```xml
<!--Use this to enable/disable recording of implicit hovers.-->
<add key="RecordImplicitHover" value="true"/>
```

## <a name="customize-the-coded-ui-test"></a>Kodlanmış UI testini özelleştirme

Kodlanmış UI testinizi oluşturduktan sonra, Visual Studio ' de aşağıdaki araçlardan herhangi birini kullanarak düzenleyebilirsiniz:

- Testlerinize ek denetimler ve doğrulama eklemek için **KODLANMıŞ UI test oluşturucusunu** kullanın. Bu konudaki [denetim ekleme ve özelliklerini doğrulama](#validate-the-properties-of-ui-controls) bölümüne bakın.

- **KODLANMıŞ UI Testi Düzenleyicisi** , kodlanmış UI testlerinizi kolayca değiştirmenize olanak sağlar. **KODLANMıŞ UI test düzenleyicisini** kullanarak test yöntemlerinizi bulabilir, görüntüleyebilir ve düzenleyebilirsiniz. UI eylemlerini ve bunlarla ilişkili denetimleri kullanıcı arabirimi denetim eşlemesinde da düzenleyebilirsiniz. Daha fazla bilgi için bkz. [kodlanmış UI test düzenleyicisini kullanarak KODLANMıŞ UI testlerini düzenleme](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).

- **Kod Düzenleyicisi:**

  - Bu konunun [KODLANMıŞ UI Denetim eylemleri ve özellikleri](#coded-ui-control-actions-and-properties) bölümünde açıklandığı gibi, testinizde denetimler için kod el ile ekleyin.

  - Kodlanmış UI testi oluşturduktan sonra, bunu veri odaklı olacak şekilde değiştirebilirsiniz. Daha fazla bilgi için bkz. [veri odaklı KODLANMıŞ UI testi oluşturma](../test/creating-a-data-driven-coded-ui-test.md).

  - Kodlanmış bir UI Testi Kayıttan yürütmede, teste bir pencere, ilerleme çubuğunun kaybolması gibi belirli olayların gerçekleşmesini beklemek için teste talimat verebilirsiniz. Bunu yapmak için, uygun UITestControl. WaitForControlXXX () metodunu ekleyin. Kullanılabilir yöntemlerin tüm listesi için bkz. [kayıttan yürütme sırasında KODLANMıŞ UI testlerinin belirli olayları beklemesini sağlama](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md). WaitForControlEnabled yöntemi kullanılarak bir denetimin etkinleştirilmesini bekleyen kodlanmış UI testinin bir örneği için bkz. [Izlenecek yol: kodlanmış BIR UI testi oluşturma, düzenlemeyle ve sürdürme](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md).

  - Kodlanmış UI testleri, Internet Explorer 9 ve Internet Explorer 10 dahil olan HTML5 denetimlerinin bazılarına yönelik destek içerir. Daha fazla bilgi için bkz. [KODLANMıŞ UI TESTLERINDE HTML5 denetimleri kullanma](../test/using-html5-controls-in-coded-ui-tests.md).

  - Kodlanmış UI test kodlama Kılavuzu:

    - [Kodlanmış UI testinin anatomumu](../test/anatomy-of-a-coded-ui-test.md)

    - [Kodlanmış UI testleri için en iyi uygulamalar](../test/best-practices-for-coded-ui-tests.md)

    - [büyük bir uygulamayı birden çok uı Haritalar Test etme](../test/testing-a-large-application-with-multiple-ui-maps.md)

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

- *UIMap. UITest* içindeki bir yöntem.

     Bu yöntem, kaydettiğiniz eylemlerin veya doğrulanmış değerin ayrıntılarını içerir. *UIMap.uitest'i açarak bu kodu düzenleyebilirsiniz.* Kayıtlı eylemleri silebilir veya yeniden düzenlemenizi istediğiniz özel bir düzenleyicide açılır.

     Oluşturulan yöntemi *UIMap.Designer.cs içinde de görüntüebilirsiniz.* Bu yöntem, testi çalıştırarak kaydettiğiniz eylemleri gerçekleştirir.

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
    > Bu dosyayı düzenlemeniz gerekir çünkü daha fazla test ederken yeniden oluşturulur.

     UiMap.cs'ye kopyalayıp bu yöntemlerin uyarlanmış *sürümlerini kullanabilirsiniz.* Örneğin, bir test yönteminden çağırarak parametreli bir sürüme sahip olabilirsiniz:

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

- *UIMap.uitest'te bildirim.*

    Bu bildirim, test tarafından kullanılan uygulamanın kullanıcı arabirimi denetimlerini temsil eder. Bunlar, oluşturulan kod tarafından denetimleri çalıştırmak ve özelliklerine erişmek için kullanılır.

    Kendi kodunuzu yazarsanız bunları da kullanabilirsiniz. Örneğin, test yönteminizin bir web uygulamasında köprü seçmesini, metin kutusuna bir değer yazmanızı veya daldan çıkararak bir alana göre farklı test eylemleri gerçekleştirebilirsiniz.

    Büyük bir uygulamayı test etmek için birden çok Kodlanmış UI testi ve birden çok kullanıcı arabirimi eşleme nesnesi ve dosyası ekebilirsiniz. Daha fazla bilgi için bkz. [Birden çok kullanıcı arabirimi ile büyük bir uygulamayı Haritalar.](../test/testing-a-large-application-with-multiple-ui-maps.md)

Oluşturulan kod hakkında daha fazla bilgi için bkz. [Kodlanmış ui testinin anatomisi.](../test/anatomy-of-a-coded-ui-test.md)

## <a name="coded-ui-control-actions-and-properties"></a>Kodlanmış UI denetim eylemleri ve özellikleri

Kodlanmış UI testlerinde UI test denetimleriyle birlikte çalışıyorken bunlar iki parçaya ayrılır: eylemler ve özellikler.

- İlk bölüm, kullanıcı arabirimi test denetimlerini gerçekleştirebilir eylemlerden oluşur. Örneğin, Kodlanmış UI testleri kullanıcı arabirimi test denetiminde fare tıklamalarını benzetebilir veya ui test denetimlerini etkilemesi için klavyede türe sahip anahtarların benzetimini yapabilirsiniz.

- İkinci bölüm, kullanıcı arabirimi test denetiminde özellik alama ve ayarlama özelliğine olanak sağlamaktır. Örneğin, Kodlanmış UI testleri, bir 'de öğe sayısını veya `ListBox` bir'i `CheckBox` seçili durum olarak ayarlıyor olabilir.

**UI Test Denetimi Eylemlerine Erişme**

Fare tıklamaları veya klavye eylemleri gibi kullanıcı arabirimi test denetimlerini gerçekleştirmek için ve sınıflarında <xref:Microsoft.VisualStudio.TestTools.UITesting.Mouse> yöntemlerini <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard> kullanın:

- Fare tıklaması gibi fare odaklı bir eylem gerçekleştirmek için kullanıcı arabirimi test denetiminde <xref:Microsoft.VisualStudio.TestTools.UITesting.Mouse.Click%2A> kullanın.

     `Mouse.Click(buttonCancel);`

- Düzenleme denetimine yazma gibi klavye odaklı bir eylem gerçekleştirmek için <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard.SendKeys%2A> kullanın.

     `Keyboard.SendKeys(textBoxDestination, @"C:\Temp\Output.txt");`

**UI Test Denetimi Özelliklerine Erişme**

Kullanıcı arabirimi denetimine özgü özellik değerlerini almak ve ayarlamak için, bir denetimin özelliklerini doğrudan almak veya ayarlamak ya da ve yöntemlerini, almak veya ayarlamak istediğiniz belirli özelliğin adıyla  <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A?displayProperty=fullName> <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A?displayProperty=fullName> kullanabilirsiniz.

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A> daha sonra uygun türüne atlandırarak bir nesnesi <xref:System.Type> döndürür. <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A> özelliğinin değeri için bir nesnesi kabul eder.

### <a name="to-get-or-set-properties-from-ui-test-controls-directly"></a>Ui test denetimlerinden özellikleri doğrudan almak veya ayarlamak için

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl> [HtmlList](xref:Microsoft.VisualStudio.TestTools.UITesting.HtmlControls.HtmlList) veya [WinComboBox](xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls.WinComboBox)gibi ' den türeyen denetimlerle, özellik değerlerini doğrudan edinebilirsiniz veya ayarlayın. Aşağıdaki kodda bazı örnekler verilmiştir:

```csharp
int i = myHtmlList.ItemCount;
myWinCheckBox.Checked = true;
```

### <a name="to-get-properties-from-ui-test-controls"></a>UI test denetimlerinden özellikleri almak için

- Bir denetimden özellik değeri almak için <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A> kullanın.

- Elde etmek için denetimin özelliğini belirtmek için, her denetimde sınıfından uygun `PropertyNames` dizeyi parametresi olarak <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A> kullanın.

- <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A> uygun veri türünü döndürür, ancak bu dönüş değeri olarak türe <xref:System.Object> döner. Daha sonra <xref:System.Object> dönüş uygun tür olarak türe dönüşe sahip olması gerekir.

     Örnek:

     `int i = (int)GetProperty(myHtmlList.PropertyNames.ItemCount);`

### <a name="to-set-properties-for-ui-test-controls"></a>UI test denetimlerinin özelliklerini ayarlamak için

- Bir denetimde özellik ayarlamak için <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A> kullanın.

- Ayar yapmak üzere denetimin özelliğini belirtmek için sınıfından uygun dizeyi birinci parametresi olarak kullanın ve ikinci parametre  `PropertyNames` <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A> olarak özellik değerini kullanın.

     Örnek:

     `SetProperty(myWinCheckBox.PropertyNames.Checked, true);`

## <a name="debug"></a>Hata Ayıklama

Kodlanmış UI test günlüklerini kullanarak Kodlanmış UI testlerini analiz edin. Kodlanmış UI test günlükleri, Kodlanmış UI test çalıştırmaları hakkında önemli bilgileri filtreler ve kaydeder. Günlüklerin biçimi sorunları hızla ayıklamaya olanak sağlar. Daha fazla bilgi için [bkz. Kodlanmış UI test günlüklerini kullanarak kodlanmış UI testlerini analiz etme.](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md)

## <a name="whats-next"></a>Sırada ne var?

::: moniker range="vs-2017"
**Kodlanmış UI testleri çalıştırmaya ek seçenekler:** Bu konuda daha önce açıklandığı gibi, kodlanmış UI Visual Studio doğrudan bir kullanıcı arabiriminden çalıştırabilirsiniz. Ayrıca, otomatik ui testlerini Microsoft Test Yöneticisi veya Azure Pipelines. Kodlanmış UI testleri otomatikleştirildiklerinde, diğer otomatikleştirilmiş testlerin aksine, bunları çalıştırarak masaüstüyle etkileşime geçmeleri gerekir.
::: moniker-end
::: moniker range=">=vs-2019"
**Kodlanmış UI testleri çalıştırmaya ek seçenekler:** Bu konuda daha önce açıklandığı gibi, kodlanmış UI Visual Studio doğrudan bir kullanıcı arabiriminden çalıştırabilirsiniz. Ayrıca, kullanıcı arabirimini kullanarak otomatik ui Azure Pipelines. Kodlanmış UI testleri otomatikleştirildiklerinde, diğer otomatikleştirilmiş testlerin aksine, bunları çalıştırarak masaüstüyle etkileşime geçmeleri gerekir.
::: moniker-end

- [Test Gezgini ile birim testleri çalıştırma](../test/run-unit-tests-with-test-explorer.md)

- [Derleme işleminizi test çalıştırma](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts&preserve-view=true)

- [Nasıl yapılacak: Test aracınızı masaüstüyle etkileşimde bulunacak testleri çalıştıracak şekilde ayarlama](/previous-versions/ee291332(v=vs.140))

**Özel denetimler için destek ekleme:**  Kodlanmış UI test çerçevesi, mümkün olan her kullanıcı arabirimini desteklemez ve test etmek istediğiniz kullanıcı arabirimini desteklemez. Örneğin, kullanıcı arabirimi için kodlanmış UI testini hemen Microsoft Excel. Ancak, özel denetimi destekleyen Kodlanmış UI test çerçevesine bir uzantı oluşturabilirsiniz.

- [Denetimlerinizin kodlanmış UI testini etkinleştirme](../test/enable-coded-ui-testing-of-your-controls.md)

- [Kodlanmış UI testlerini ve eylem kayıtlarını genişletme](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)

Kodlanmış UI testleri genellikle el ile testleri otomatikleştirmek için kullanılır. Otomatikleştirilmiş testler hakkında daha fazla bilgi için bkz. [Visual Studio.](../test/improve-code-quality.md)

## <a name="see-also"></a>Ayrıca bkz.

- [El ile yapılan testleri kaydetme ve kayıtdan oynatma](/azure/devops/test/mtm/record-play-back-manual-tests?view=vsts&preserve-view=true)
- [Xamarin.UITest](/appcenter/test-cloud/uitest/)
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>
- [Adım adım kılavuz: Kodlanmış ui testi oluşturma, düzenleme ve sürdürme](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
- [UWP uygulamasını test etmek için Kodlanmış UI testi oluşturma](test-uwp-app-with-coded-ui-test.md)
- [Kodlanmış UI testinin anatomisi](../test/anatomy-of-a-coded-ui-test.md)
- [Kodlanmış UI testleri için en iyi yöntemler](../test/best-practices-for-coded-ui-tests.md)
- [Büyük bir uygulamayı birden çok kullanıcı arabirimi arabirimiyle Haritalar](../test/testing-a-large-application-with-multiple-ui-maps.md)