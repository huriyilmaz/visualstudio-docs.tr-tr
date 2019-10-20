---
title: Kodunuzu test etmek Için UI Otomasyonunu kullanma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
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
ms.assetid: ad9e3eaa-ab86-436e-95b8-dc20eb1f8b2a
caps.latest.revision: 87
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 070a9bedd5e01e6c39d55d784559d4458e35d72f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657286"
---
# <a name="use-ui-automation-to-test-your-code"></a>Kodunuzu Test Etmek için UI Otomasyonunu Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uygulamanızı Kullanıcı arabirimi (UI) aracılığıyla hedefleyen otomatikleştirilmiş testler, *KODLANMıŞ UI testleri* (cuits) olarak bilinir. Bu sınamalar, UI denetimlerinin işlevsel sınamasını içerir. Bu kişiler, Kullanıcı arabirimi de dahil olmak üzere tüm uygulamanın doğru şekilde çalıştığını doğrulamanızı sağlar. Kodlanmış UI testleri özellikle Kullanıcı arabiriminde doğrulama veya başka bir mantık olduğu durumlarda (örneğin, bir Web sayfasında) yararlıdır. Ayrıca, var olan bir el ile testi otomatikleştirmek için sık kullanılır.

 Aşağıdaki çizimde gösterildiği gibi tipik bir geliştirme deneyimi, başlangıçta uygulamanızı derlemenize (F5) ve nesnelerin doğru şekilde çalıştığını doğrulamak için UI denetimlerine tıklamanız durumunda olabilir. Daha sonra, uygulamayı el ile test etmeye devam etmeniz gerekmiyorsa, kodlanmış bir test oluşturmaya karar verebilirsiniz. Uygulamanızda test edilmekte olan belirli işlevlere bağlı olarak, işlevsel bir test için veya test Kullanıcı arabirimi düzeyinde test içerme gerektirebilecek ya da içeremeyebilir bir tümleştirme testi için kod yazabilirsiniz. Yalnızca bazı iş mantığına doğrudan erişmek istiyorsanız bir birim testini kodda edebilirsiniz. Ancak bazı durumlarda, uygulamanıza çeşitli UI denetimlerinin test edilmesi yararlı olabilir. Kodlanmış bir UI testi, ilk (F5) senaryoyu otomatikleştirebilir, bu da kod karmaşıklığının uygulamanızın işlevselliğini etkilemediğinden emin olur.

 ![Uygulama geliştirme sırasında test etme](../test/media/cuit-overview.png "CUIT_Overview")

 Kodlanmış UI testi oluşturmak kolaydır. CUıT Test Oluşturucusu arka planda çalışırken testi yalnızca el ile gerçekleştirirsiniz. Ayrıca, belirli alanlarda görüntülenecek değerleri de belirtebilirsiniz. CUıT Test Oluşturucusu eylemlerinizi kaydeder ve bunlardan kod oluşturur. Test oluşturulduktan sonra, eylem dizisini değiştirmenize olanak sağlayan özelleştirilmiş bir düzenleyicide düzenleyebilirsiniz.

 Alternatif olarak, Microsoft Test Yöneticisi kaydedilmiş bir test çalışmanıza sahipseniz, bundan kod oluşturabilirsiniz. Daha fazla bilgi için bkz. [el ile testleri kaydetme ve kayıttan yürütme](/azure/devops/test/mtm/record-play-back-manual-tests).

 Özelleştirilmiş CUıT Test Oluşturucusu ve Düzenleyicisi, ana becerilerinizi kodlama yerine test halinde yoğunlaşsa bile kodlanmış UI testlerini oluşturmayı ve düzenlemenizi kolaylaştırır. Ancak bir geliştiricisiyseniz ve testi daha gelişmiş bir şekilde genişletmek istiyorsanız, kod yapılandırılmıştır ve uyarlanabilmesi için yapılandırılır. Örneğin, bir Web sitesinde bir şey satın almak için bir test kaydedebilir ve sonra çok sayıda öğe alan bir döngü eklemek için oluşturulan kodu düzenleyebilirsiniz.

 **Requirements**

- Visual Studio Enterprise

  Kodlanmış UI testleri tarafından desteklenen platformlar ve Konfigürasyonlar hakkında daha fazla bilgi için bkz. [KODLANMıŞ UI testleri ve eylem kayıtları Için desteklenen konfigürasyonlar ve platformlar](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md).

  **Bu konuda**

- [Kodlanmış UI testleri oluşturma](#VerifyingCodeUsingCUITCreate)

  - [Ana yordam](#VerifyingCodeUsingCUITCreate)

  - [Uygulamayı başlatma ve durdurma](#starting)

  - [UI denetimlerinin özelliklerini doğrulama](#VerifyingCodeUsingCUITGenerateAssertions)

- [Kodlanmış UI testinizi özelleştirme](#VerifyingCodeCUITModify)

  - [Oluşturulan kod](#generatedCode)

  - [UI denetim eylemlerini ve özelliklerini kodlama](#actions)

  - [Hata Ayıklama](#debugging)

- [Sıradaki](#VerifyCodeUsingCUITWhatsNext)

## <a name="VerifyingCodeUsingCUITCreate"></a>Kodlanmış UI testleri oluşturma

1. **Kodlanmış UI test projesi oluşturun.**

    Kodlanmış UI testleri kodlanmış UI testi projesinde bulunmalıdır. Zaten kodlanmış bir UI test projeniz yoksa, bir tane oluşturun. **Çözüm Gezgini**, çözümün kısayol menüsünde, **Ekle**, **Yeni proje** ' yi seçin ve sonra **Visual Basic** veya **görsel C#** ' ü seçin. Sonra **Test**, **kodlanmış UI testi**öğesini seçin.

   - <em> **KODLANMıŞ UI test</em>* projesi şablonlarını göremiyorum.*

      Kodlanmış UI testlerini desteklemeyen bir Visual Studio sürümü kullanıyor olabilirsiniz. Kodlanmış UI testleri oluşturmak için Visual Studio Enterprise kullanmanız gerekir.

2. **Kodlanmış UI test dosyası ekleyin.**

    Yalnızca kodlanmış bir UI projesi oluşturduysanız, ilk CUIT dosyası otomatik olarak eklenir. Başka bir test dosyası eklemek için, kodlanmış UI testi projesinde kısayol menüsünü açın, **Ekle**' nin üzerine gelin ve **kodlanmış UI testi**' ni seçin.

    ![Kodlanmış UI testi oluşturma](../test/media/codedui-create.png "CodedUI_Create")

    **KODLANMıŞ UI testi Için kod üret** iletişim kutusunda, **EYLEMLERI Kaydet, UI haritasını Düzenle veya onaylama Ekle**' yi seçin.

    ![Kayıt eylemlerini seçin](../test/media/codedui-codegendialogb.png "CodedUI_CodeGenDialogB")

    Kodlanmış UI Test Oluşturucusu görünür ve Visual Studio simge durumuna küçültülmüş.

    ![Kodlanmış UI Test Oluşturucusu](../test/media/codedui-testbuilder.png "CodedUI_TestBuilder")

3. **Bir dizi eylemi kaydedin**.

    **Kaydı başlatmak Için** **kayıt** simgesini seçin. Uygulamanızda test etmek istediğiniz eylemleri, bu gerekliyse uygulamayı başlatma dahil olmak üzere gerçekleştirin.

    Örneğin, bir Web uygulamasını test ediyorsanız, bir tarayıcı başlatabilir, Web sitesine gidebilir ve uygulamada oturum açmanız gerekebilir.

    **Kaydı duraklatmak için**Örneğin, gelen posta ile uğraşmanız gerekiyorsa, **Duraklat**' ı seçin.

   > [!WARNING]
   > Masaüstünde gerçekleştirilen tüm eylemler kaydedilir. Kayıt sırasında hassas verilerin oluşmasına neden olabilecek eylemler gerçekleştiriyorsanız kaydı duraklatın.

    Yanlışlıkla kaydettiğiniz **eylemleri silmek için** , **eylemleri Düzenle**' yi seçin.

    Eylemlerinizi çoğaltan **kodu oluşturmak Için** **kod oluştur** SIMGESINI seçin ve kodlanmış UI Test yönteminiz için bir ad ve açıklama yazın.

4. **Metin kutuları gibi kullanıcı arabirimi alanlarındaki değerleri doğrulayın**.

    Kodlanmış UI Test Oluşturucusu 'nda **onaylama Ekle** ' yi seçin ve ardından çalışan UYGULAMANıZDA bir UI denetimi seçin. Görüntülenen özellikler listesinde, bir metin kutusundaki **metin** gibi bir özellik seçin. Kısayol menüsünde **onay Ekle**' yi seçin. İletişim kutusunda karşılaştırma işlecini, karşılaştırma değerini ve hata iletisini seçin.

    Onaylama penceresini kapatın ve **kod üret**' i seçin.

    ![Kodlanmış UI test hedefleme öğesi](../test/media/codedui-1.png "CodedUI_1")

   > [!TIP]
   > Kaydetme eylemleri ve değerleri doğrulama arasında alternatif. Her eylem veya doğrulama dizisinin sonunda kod oluşturun. İsterseniz, yeni eylemleri ve doğrulamaları daha sonra ekleyebileceksiniz.

    Daha ayrıntılı bilgi için bkz. [denetimlerin özelliklerini doğrulama](#VerifyingCodeUsingCUITGenerateAssertions).

5. **Oluşturulan test kodunu görüntüleyin**.

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

6. **Daha fazla eylem ve onaylama ekleyin**.

    İmleci test yönteminde uygun noktaya yerleştirin ve ardından kısayol menüsünde, **KODLANMıŞ UI testi Için kod üret**' i seçin. Yeni kod bu noktaya eklenecektir.

7. **Test eylemlerinin ve onayların ayrıntılarını düzenleyin**.

    UIMap. UITest öğesini açın. Bu dosya, kodlanmış UI Test Düzenleyicisi 'nde açılır. burada, kaydettiğiniz herhangi bir işlem dizisini düzenleyebilir ve onaylarınızı düzenleyebilirsiniz.

    ![Kodlanmış UI Test Düzenleyicisi](../test/media/cuit-editor-edit.png "CUIT_Editor_edit")

    Daha fazla bilgi için bkz. [kodlanmış UI test düzenleyicisini kullanarak KODLANMıŞ UI testlerini düzenleme](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).

8. **Testi çalıştırın**.

    Test Gezgini 'ni kullanın veya test yönteminde kısayol menüsünü açın ve **Testleri Çalıştır**' ı seçin. Testlerin nasıl çalıştırılacağı hakkında daha fazla bilgi için, bkz. [Test Gezgini ile birim testlerini çalıştırma](../test/run-unit-tests-with-test-explorer.md) ve bu konunun sonundaki [sonraki nedir?](#VerifyCodeUsingCUITWhatsNext) bölümünde *kodlanmış UI testlerini çalıştırmak için ek seçenekler* .

   Bu konudaki geri kalan bölümler, bu yordamdaki adımlar hakkında daha fazla ayrıntı sağlar.

   Daha ayrıntılı bir örnek için bkz. [Izlenecek yol: kodlanmış BIR UI testi oluşturma, düzenlemeyle ve sürdürme](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md). İzlenecek yolda, kodlanmış UI testinin nasıl oluşturulduğunu, düzenleneceğini ve bakımının nasıl yapılacağını göstermek için basit bir Windows Presentation Foundation (WPF) uygulaması oluşturacaksınız. İzlenecek yol çeşitli zamanlama sorunları ve yeniden düzenlemeyi denetleme tarafından kırılan testleri düzeltmeye ilişkin çözümler sağlar.

### <a name="starting"></a>Test edilen uygulamayı başlatma ve durdurma
 *Uygulama, tarayıcı veya veritabanını her test için ayrı olarak başlatmak ve durdurmak istemiyorum. Nasıl yaparım? bunun oluşmaması mi?*

- ![Prerequsite](../test/media/prereq.png "Önkoşul") Uygulamanızı test altına başlatmak üzere eylemleri kaydetmek istemiyorsanız, **kayıt** simgesini seçmeden önce uygulamanızı başlatmanız gerekir.

- ![Prerequsite](../test/media/prereq.png "Önkoşul") Testin sonunda, testin çalıştırıldığı işlem sonlandırılır. Uygulamanızı testte başlattıysanız uygulama genellikle kapanır.  Testin, çıkış sırasında uygulamanızı kapatmasını istemiyorsanız, çözümünüze bir. runsettings dosyası eklemeniz ve `KeepExecutorAliveAfterLegacyRun` seçeneğini kullanmanız gerekir. Daha fazla bilgi için bkz [. runsettings dosyasını kullanarak birim testlerini yapılandırma](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).

- ![Prerequsite](../test/media/prereq.png "Önkoşul") Her test yönteminin başlangıcında kodu çalıştıran bir [TestInitialize] özniteliğiyle tanımlanan bir test Initialize yöntemi ekleyebilirsiniz. Örneğin, uygulamayı TestInitialize yönteminden başlatabilirsiniz.

- ![Prerequsite](../test/media/prereq.png "Önkoşul") Her test yönteminin sonunda kodu çalıştıran bir [TestCleanup] özniteliğiyle tanımlanan bir test temizleme yöntemi ekleyebilirsiniz. Örneğin, uygulamayı kapatmak için yöntemi TestCleanup yönteminden çağrılabilir.

### <a name="VerifyingCodeUsingCUITGenerateAssertions"></a>UI denetimlerinin özelliklerini doğrulama
 Test için [UIMap](/previous-versions/dd580454(v=vs.140)) 'e bir kullanıcı ARABIRIMI (UI) denetimi eklemek veya bir UI denetimi için onay kullanan bir doğrulama yöntemi için kod oluşturmak üzere **kodlanmış UI test oluşturucusunu** kullanabilirsiniz.

 UI Denetimleriniz için onay oluşturmak için, kodlanmış UI Test Oluşturucusu 'nda **onaylama Ekle** aracını seçin ve test edilen uygulamanın altındaki denetime doğru bir şekilde, doğrulamak istediğiniz denetime sürükleyin. Kutu denetiminizi özetler, fare düğmesini bırakın. Denetim sınıfı kodu `UIMap.Designer.cs` dosyasında hemen oluşturulur.

 ![Kodlanmış UI test hedefleme öğesi](../test/media/codedui-1.png "CodedUI_1")

 Bu denetimin özellikleri artık onaylar **Ekle** iletişim kutusunda listelenir.

 Belirli bir denetime gitmenin bir diğer yolu da, **Kullanıcı arabirimi denetim eşlemesi**görünümünü genişletmek için oku **(< <)** kullanmaktır. Üst, eşdüzey veya alt denetim bulmak için haritada herhangi bir yere tıklayabilir ve ok tuşlarını kullanarak ağaç etrafında hareket edebilirsiniz.

 ![Kodlanmış UI testi özellikleri](../test/media/codedui-2.png "CodedUI_2")

- *Uygulamamda bir denetim seçdiğimde hiçbir özellik görmüyorum veya denetimi UI denetim haritasında görmüyorum.*

   Uygulama kodunda, doğrulamak istediğiniz denetim, bir HTML ID özniteliği veya bir WPF UId gibi benzersiz bir KIMLIĞE sahip olmalıdır. Bu kimlikleri eklemek için uygulama kodunu güncelleştirmeniz gerekebilir.

  Daha sonra, doğrulamak istediğiniz UI denetiminin özelliğindeki kısayol menüsünü açın ve **onaylama Ekle**' ye gelin. **Onaylama Ekle** iletişim kutusunda, onayınız için **karşılaştırıcı** ' yı seçin (örneğin <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A>) ve bir **karşılaştırma değerinde**onayınız için değeri yazın.

  ![Kodlanmış UI testi onayları](../test/media/codedui-3.png "CodedUI_3")

  Testiniz için tüm onaylarınızı eklediğinizde **Tamam**' ı seçin.

  Onaylarınız için kod oluşturmak ve Kullanıcı arabirimi eşlemesine denetim eklemek için **kod oluştur** simgesini seçin. Kodlanmış UI Test yönteminiz için bir ad ve yöntem için açıklama olarak eklenecek Yöntem için bir açıklama yazın. **Ekle ve Oluştur '** a tıklayın. Sonra, **KODLANMıŞ UI Test Oluşturucusu**'nu kapatmak için **Kapat** simgesini seçin. Bu, aşağıdaki koda benzer bir kod üretir. Örneğin, girdiğiniz ad `AssertForAddTwoNumbers`, kod şu örneğe benzer şekilde görünür:

- AssertForAddTwoNumbers onaylama yöntemine, kodlanmış UI test dosyanızdaki test yöntemine bir çağrı ekler:

  ```
  [TestMethod]
  public void CodedUITestMethod1()
  {
      this.UIMap.AddTwoNumbers();
      this.UIMap.AssertForAddTwoNumbers();
  }
  ```

   Adımların ve onayların sırasını değiştirmek veya yeni test yöntemleri oluşturmak için bu dosyayı düzenleyebilirsiniz. Daha fazla kod eklemek için, imleci test yöntemine yerleştirin ve kısayol menüsünde, **KODLANMıŞ UI testi Için kod oluştur**' u seçin.

- UI haritanızda `AssertForAddTwoNumbers` adlı bir yöntem ekler (UIMap. UITest). Bu dosya, onayları düzenleyebileceğiniz, kodlanmış UI Test Düzenleyicisi 'nde açılır.

   ![Kodlanmış UI test düzenleyicisini kullanarak onayı düzenleme](../test/media/cuit-editor-assert.png "CUIT_Editor_assert")

   Daha fazla bilgi için bkz. [kodlanmış UI test düzenleyicisini kullanarak KODLANMıŞ UI testlerini düzenleme](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).

   Ayrıca, UIMap.Designer.cs içinde onay yönteminin oluşturulan kodunu görüntüleyebilirsiniz. Ancak, bu dosyayı düzenlememelisiniz. Kodun uyarlanan bir sürümünü yapmak istiyorsanız, yöntemleri UIMap.cs gibi başka bir dosyaya kopyalayın, yöntemleri yeniden adlandırın ve orada düzenleyin.

  ```
  public void AssertForAddTwoNumbers()
  {
      ...
  }
  ```

  *Seçme istediğim denetim, KODLANMıŞ UI Test Oluşturucusu 'Ndan onaylama Ekle aracını seçmeyi denediğimde odağı kaybeder ve kaybolur. Nasıl yaparım? denetimi mi seçmelisiniz?* **klavyeyi kullanarak gizli bir denetim seçme** 
  

  Bazen, [denetimleri eklerken ve özelliklerini doğrularken](#VerifyingCodeUsingCUITGenerateAssertions), klavyeyi kullanmanız gerekebilir. Örneğin, bir bağlam menüsü denetimi kullanan kodlanmış bir UI testini kaydetmeye çalıştığınızda, denetimdeki menü öğelerinin listesi odağı kaybeder ve kodlanmış UI Test Oluşturucusu 'ndan onaylama Ekle aracını seçmeyi denediğinizde kaybolur. Bu, Internet Explorer 'daki bağlam menüsünün odağı kaybedeceğinizi ve onay Ekle aracıyla seçmeyi denerseniz kaybolur.

  ![CodedUITest&#95;selectcontrolkeyboard](../test/media/codeduitest-selectcontrolkeyboard.png "CodedUITest_SelectControlKeyboard")

  Bir UI denetimi seçmek üzere klavyeyi kullanmak için fare ile denetimin üzerine gelin. Ardından **CTRL** tuşunu ve **ı** tuşunu aynı anda basılı tutun. Anahtarları serbest bırakın. Denetim, kodlanmış UT Test Oluşturucusu tarafından kaydedilir.

> [!WARNING]
> Microsoft Lync kullanıyorsanız, kodlanmış UI Test Oluşturucusu 'nu başlamadan önce Lync 'i kapatmanız gerekir. Microsoft Lync, **CTRL + I** klavye kısayolunu ile kesintiye uğratır.

 *Bir denetime fare ile gidilme kaydedemiyorum. Bunun etrafında bir yol var mı?*
 **Fareyi el ile kaydetme gezdirme**

 Bazı durumlarda, kodlanmış UI testinde kullanılan belirli bir denetim, fare üzerine gelme olaylarını el ile kaydetmek için klavyeyi kullanmanızı gerektirebilir. Örneğin, bir Windows formunu veya Windows Presentation Foundation (WPF) uygulamasını test ettiğinizde özel kod olabilir. Ya da, bir denetimin üzerine gelindiğinde, bir kullanıcı onun üzerine geldiğinde genişleyen bir ağaç düğümü gibi özel davranışlar tanımlanmış olabilir. Bunlar gibi durumları test etmek için, önceden tanımlanmış klavye tuşlarına basarak, denetimin üzerine geldiğinizde kodlanmış UI Test Oluşturucusu 'nu el ile bilgilendirmeniz gerekir.

 Kodlanmış UI testinizi gerçekleştirdiğinizde, denetimin üzerine gelin. Ardından, klavyenizde Shift ve R tuşlarını basılı tutarken CTRL tuşunu basılı tutun. Anahtarları serbest bırakın. Bir fare üzerine gelme olayı, kodlanmış UT Test Oluşturucusu tarafından kaydedilir.

 ![CodedUI&#95;üzerine gelme](../test/media/codedui-hover.png "CodedUI_Hover")

 Test yöntemini oluşturduktan sonra, aşağıdaki örneğe benzer bir kod UIMap.Desinger.cs dosyasına eklenecektir:

```csharp
// Mouse hover '1' label at (87, 9)
Mouse.Hover(uIItem1Text, new Point(87, 9));

```

 *Fare üzerine gelme olaylarını yakalamaya yönelik anahtar atama, ortamınızda başka bir yerde kullanılıyor. Varsayılan anahtar atamasını değiştirebilir miyim?*
 **Fare üzerine gelme klavye atamalarını yapılandırma**

 Gerekirse, kodlanmış UI testlerinizde fare vurgulama olaylarını uygulamak için kullanılan varsayılan klavye ataması, farklı anahtarlar kullanacak şekilde yapılandırılabilir.

> [!WARNING]
> Normal koşullarda fare üzerine gelme olayları için klavye atamalarını değiştirmeniz gerekmez. Klavye atamasını yeniden atayarak dikkatli olun. Seçiminiz, Visual Studio içinde başka bir yerde veya test edilmekte olan uygulamanın zaten kullanılıyor olabilir.

 Klavye atamalarını değiştirmek için aşağıdaki yapılandırma dosyasını değiştirmeniz gerekir:

 `<drive letter:>\Program Files (x86)\Microsoft Visual Studio 11.0\Common7\IDE\CodedUITestBuilder.exe.config`

 Yapılandırma dosyasında, klavye atamalarını değiştirmek için `HoverKeyModifier` ve `HoverKey` anahtarlarının değerlerini değiştirin:

```
<!-- Begin : Background Recorder Settings -->
<!-- HoverKey to use. -->
<add key="HoverKeyModifier" value="Control, Shift"/>
<add key="HoverKey" value="R"/>

```

 *Kayıt faresi ile ilgili bir Web sitesinde sorun yaşıyorum. Bunun için de bir çözüm var mı?*
 **Web tarayıcısı için örtük fare imlecini ayarlama**

 Birçok Web sitesinde, belirli bir denetimin üzerine geldiğinizde, ek ayrıntıları göstermek için genişler. Genellikle bu, masaüstü uygulamalarında menüler gibi görünür. Bu ortak bir model olduğundan, kodlanmış UI testleri Web 'e göz atmaya yönelik örtülü olarak dolaşmasını etkinleştirir. Örneğin, Internet Explorer 'da geldiğinde kayıt yaparsanız bir olay tetiklenir. Bu olaylar, kaydedilen sonuçlara yol açabilir. Bu nedenle, örtük olarak, Kullanıcı arabirimi test yapılandırma dosyasında `true` olarak ayarlanmış `ContinueOnError` kaydedilir. Bu, bir vurgulama olayı başarısız olursa kayıttan yürütmenin devam etmesine olanak tanır.

 Bir Web tarayıcısında örtük olarak bekletilme kaydını etkinleştirmek için yapılandırma dosyasını açın:

 `<drive letter:>\Program Files (x86)\Microsoft Visual Studio 11.0\Common7\IDE\CodedUITestBuilder.exe.config`

 Aşağıdaki örnekte gösterildiği gibi, yapılandırma dosyasının anahtar `RecordImplicitiHovers` bir `true` değerine ayarlandığını doğrulayın:

```
<!--Use this to enable/disable recording of implicit hovers.-->
<add key="RecordImplicitHover" value="true"/>

```

## <a name="VerifyingCodeCUITModify"></a>Kodlanmış UI testinizi özelleştirme
 Kodlanmış UI testinizi oluşturduktan sonra, Visual Studio 'da aşağıdaki araçlardan herhangi birini kullanarak düzenleyebilirsiniz:

- **KODLANMıŞ UI Test Oluşturucusu:** Testlerinize ek denetimler ve doğrulama eklemek için kodlanmış UI test oluşturucusunu kullanın. Bu konudaki [denetim ekleme ve özelliklerini doğrulama](#VerifyingCodeUsingCUITGenerateAssertions) bölümüne bakın.

- **KODLANMıŞ UI Test Düzenleyicisi:** Kodlanmış UI Testi Düzenleyicisi, kodlanmış UI testlerinizi kolayca değiştirmenize olanak sağlar. Kodlanmış UI test düzenleyicisini kullanarak test yöntemlerinizi bulabilir, görüntüleyebilir ve düzenleyebilirsiniz. UI eylemlerini ve bunlarla ilişkili denetimleri kullanıcı arabirimi denetim eşlemesinde da düzenleyebilirsiniz. Daha fazla bilgi için bkz. [kodlanmış UI test düzenleyicisini kullanarak KODLANMıŞ UI testlerini düzenleme](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).

- **Kod Düzenleyicisi:**

  - Bu konunun [UI Denetim eylemleri ve özellikleri](#actions) bölümünde açıklandığı gibi, testinizde denetimler için kod el ile ekleyin.

  - Kodlanmış UI testi oluşturduktan sonra, bunu veri odaklı olacak şekilde değiştirebilirsiniz. Daha fazla bilgi için bkz. [veri odaklı KODLANMıŞ UI testi oluşturma](../test/creating-a-data-driven-coded-ui-test.md).

  - Kodlanmış bir UI Testi Kayıttan yürütmede, teste bir pencere, ilerleme çubuğunun kaybolması gibi belirli olayların gerçekleşmesini beklemek için teste talimat verebilirsiniz. Bunu yapmak için, uygun UITestControl. WaitForControlXXX () metodunu ekleyin. Kullanılabilir yöntemlerin tüm listesi için bkz. [kayıttan yürütme sırasında belirli olaylar Için KODLANMıŞ UI testlerini bekleme](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md). WaitForControlEnabled yöntemi kullanılarak bir denetimin etkinleştirilmesini bekleyen kodlanmış UI testinin bir örneği için bkz. [Izlenecek yol: kodlanmış BIR UI testi oluşturma, düzenlemeyle ve sürdürme](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md).

  - Kodlanmış UI testleri, Internet Explorer 9 ve Internet Explorer 10 ' da bulunan HTML5 denetimlerinin bazılarına yönelik destek içerir. Daha fazla bilgi için bkz. [KODLANMıŞ UI TESTLERINDE HTML5 denetimleri kullanma](../test/using-html5-controls-in-coded-ui-tests.md).

  - **Kodlanmış UI test kodlama Kılavuzu:**

    - [Kodlanmış UI Testinin Anatomisi](../test/anatomy-of-a-coded-ui-test.md)

    - [Kodlanmış UI Testleri için En İyi Yöntemler](../test/best-practices-for-coded-ui-tests.md)

    - [Birden Çok UI Eşlemesi Bulunan Büyük Uygulamaları Sınama](../test/testing-a-large-application-with-multiple-ui-maps.md)

    - [Kodlanmış UI Testleri ve Eylem Kayıtları için Desteklenen Yapılandırmalar ve Platformlar](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)

### <a name="generatedCode"></a>Oluşturulan kod
 **Kod oluştur**' u seçtiğinizde, çeşitli kod parçaları oluşturulur:

- **Test yönteminde bir çizgi.**

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

- **UIMap. UITest içindeki bir yöntem**

   Bu yöntem, kaydettiğiniz eylemlerin veya doğrulamış olduğunuz değerin ayrıntılarını içerir. UIMap. UITest ' i açarak bu kodu düzenleyebilirsiniz. Kayıtlı eylemleri silebilmeniz veya yeniden düzenleyebileceğiniz özelleştirilmiş bir düzenleyicide açılır.

   Ayrıca, UIMap.Designer.cs içinde oluşturulan yöntemi görüntüleyebilirsiniz. Bu yöntem, testi çalıştırdığınızda kaydettiğiniz eylemleri gerçekleştirir.

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

   Bu yöntemlerin uyarlanan sürümlerini UIMap.cs 'e kopyalayarak yapabilirsiniz. Örneğin, bir test yönteminden çağırabilmeniz için parametreli bir sürüm yapabilirsiniz:

  ```csharp
  // File: UIMap.cs
  public partial class UIMap // Same partial class
  {
    /// <summary>
    /// Add two numbers – parameterized version
    /// </summary>
    public void AddTwoNumbers(int firstNumber, int secondNumber)
    { ...   // Code modified to use parameters.
    }
  }
  ```

- **UIMap. UITest içindeki bildirimler**

   Bu bildirimler, testinizin kullandığı uygulamanın kullanıcı arabirimi denetimlerini temsil eder. Bunlar, denetimleri çalıştırmak ve özelliklerine erişmek için oluşturulan kod tarafından kullanılır.

   Ayrıca, kendi kodunuzu yazarsanız de kullanabilirsiniz. Örneğin, test yönteminizin bir Web uygulamasında köprü seçmesini, bir metin kutusuna bir değer yazmasını veya bir alandaki bir değere göre farklı test eylemleri ele geçirmesine sahip olabilirsiniz.

   Büyük bir uygulamanın test edilmesini kolaylaştırmak için birden çok kodlanmış UI testi ve birden çok UI eşlemesi nesnesi ve dosyası ekleyebilirsiniz. Daha fazla bilgi için bkz. [birden çok UI haritası Ile büyük bir uygulamayı test etme](../test/testing-a-large-application-with-multiple-ui-maps.md).

  Oluşturulan kod hakkında daha fazla bilgi için bkz. [KODLANMıŞ UI testinin Anatomy](../test/anatomy-of-a-coded-ui-test.md).

### <a name="actions"></a>UI denetim eylemlerini ve özelliklerini kodlama
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

##### <a name="to-get-or-set-properties-from-ui-test-controls-directly"></a>UI test denetimlerinden doğrudan özellik almak veya ayarlamak için

- T:Microsoft.VisualStudio.TestTools.UITesting.HtmlControls.HtmlList veya T gibi T:Microsoft.VisualStudio.TestTools.UITesting.UITestControl öğesinden türetilen denetimlerle: Microsoft. VisualStudio. TestTools. Uıitedıal. WinControls. WinComboBox, özellik değerlerini doğrudan alabilir veya aşağıdaki gibi ayarlayabilirsiniz:

    ```
    int i = myHtmlList.ItemCount;
    myWinCheckBox.Checked = true;
    ```

##### <a name="to-get-properties-from-ui-test-controls"></a>UI test denetimlerinden özellikleri almak için

- Bir denetimden Özellik değeri almak için <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A> kullanın.

- Alınacak denetimin özelliğini belirtmek için, <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A> parametresi olarak her denetimdeki `PropertyNames` sınıftan uygun dizeyi kullanın.

- <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A> uygun veri türünü döndürür, ancak bu dönüş değeri bir <xref:System.Object> olarak dönüştürüldü. Dönüş <xref:System.Object> uygun tür olarak yayınlanmalıdır.

     Örnek:

     `int i = (int)GetProperty(myHtmlList.PropertyNames.ItemCount);`

##### <a name="to-set-properties-for-ui-test-controls"></a>UI test denetimleri için özellikleri ayarlamak için

- Bir denetimdeki özelliği ayarlamak için <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A> kullanın.

- Ayarlanacak denetimin özelliğini belirtmek için, ikinci parametre olarak özellik değeri ile, `PropertyNames` sınıfından <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A> ilk parametre olarak uygun dizeyi kullanın.

     Örnek:

     `SetProperty(myWinCheckBox.PropertyNames.Checked, true);`

### <a name="debugging"></a> Hata Ayıklama
 Kodlanmış UI test günlüklerini kullanarak kodlanmış UI testlerini çözümleyebilirsiniz. Kodlanmış UI test günlükleri, kodlanmış UI test çalışmalarınız hakkında önemli bilgileri filtreleyip kaydeder. Günlüklerin biçimi sorunları hızlı bir şekilde ayıklamanıza olanak tanır. Daha fazla bilgi için bkz. [kodlanmış UI test günlüklerini kullanarak KODLANMıŞ UI testlerini çözümleme](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md).

## <a name="VerifyCodeUsingCUITWhatsNext"></a>Sırada ne var?
 **KODLANMıŞ UI testlerini çalıştırmak Için ek seçenekler:** Kodlanmış UI testlerini, bu konuda daha önce açıklandığı gibi doğrudan Visual Studio 'dan çalıştırabilirsiniz. Ayrıca, [!INCLUDE[TCMext](../includes/tcmext-md.md)] veya [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] otomatik UI testleri çalıştırabilirsiniz. Kodlanmış UI testleri otomatikleştirildiğinde, diğer otomatikleştirilmiş testlerin aksine, bunları çalıştırdığınızda masaüstüyle etkileşim kurması gerekir.

- [Nasıl yapılır: Microsoft Visual Studio Testleri çalıştırma](https://msdn.microsoft.com/library/1a1207a9-2a33-4a1e-a1e3-ddf0181b1046)

- [Microsoft Test Yöneticisi içinde otomatikleştirilmiş testleri çalıştırma](https://msdn.microsoft.com/0632f265-63fe-4859-a413-9bb934c66835)

- [Nasıl yapılır: uygulamanızı oluşturduktan sonra Zamanlanmış Testleri Yapılandırma ve çalıştırma](https://msdn.microsoft.com/32acfeb1-b1aa-4afb-8cfe-cc209e6183fd)

- [Yapı sürecinizdeki testleri çalıştırın](https://msdn.microsoft.com/library/d05743a1-c5cf-447e-bed9-bed3cb595e38)

- [Komut satırından otomatikleştirilmiş testleri çalıştırma](https://msdn.microsoft.com/library/f18179c6-b688-4e41-9898-8aca130c4fc3)

- [Nasıl yapılır: Masaüstü ile etkileşimi olan testleri çalıştırmak için test aracınızı ayarlama](/visualstudio/test/how-to-set-up-your-test-agent-to-run-tests-that-interact-with-the-desktop?view=vs-2015)

- [&#91;Yük&#93; TESTLERINDE kodlanmış UI testleri kullanılarak kullanımdan kaldırıldı](https://msdn.microsoft.com/library/704339ff-7da7-4d5f-acb3-c3b23f4acb43)

  **Özel denetimler için destek ekleme:**  Kodlanmış UI test çerçevesi olası her kullanıcı arabirimini desteklemez ve test etmek istediğiniz kullanıcı arabirimini desteklemeyebilir. Örneğin, [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] için Kullanıcı arabiriminin kodlanmış UI testini hemen oluşturamazsınız. Ancak, kodlanmış UI test çerçevesine özel bir denetimi destekleyecek bir uzantı oluşturabilirsiniz.

- [Denetimlerinizin Kodlanmış UI Testlerini Etkinleştirme](../test/enable-coded-ui-testing-of-your-controls.md)

- [Kodlanmış Kullanıcı Arabirimi Testlerini ve Eylem Kayıtlarını Microsoft Excel'i Desteklemek için Genişletme](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)

  Kodlanmış UI testleri, genellikle el ile testleri otomatikleştirmek için kullanılır. Ek rehberlik için bkz. [Visual Studio Ile sürekli teslim Için test etme 2012 – Bölüm 5: Sistem testlerini otomatikleştirme](http://go.microsoft.com/fwlink/?LinkID=255196). El ile testler hakkında daha fazla bilgi için [ &#91;bkz&#93; . Microsoft Test Yöneticisi kullanarak el ile test çalışmaları oluşturma](https://msdn.microsoft.com/library/9989e184-c8e4-444b-998d-a1a5ec94461e). Otomatik sistem testleri hakkında daha fazla bilgi için bkz. [Microsoft Test Yöneticisi kullanarak otomatikleştirilmiş testler oluşturma](https://msdn.microsoft.com/7b5075ee-ddfe-411d-b1d4-94283550a5d0).

## <a name="external-resources"></a>Dış Kaynaklar

### <a name="guidance"></a>Kılavuz
- [Visual Studio 2012 ile sürekli teslim için test etme – Bölüm 2: birim testi: Içini test etme](http://go.microsoft.com/fwlink/?LinkID=255188)

- [Visual Studio 2012 ile sürekli teslim için test etme – Bölüm 5: Sistem testlerini otomatikleştirme](http://go.microsoft.com/fwlink/?LinkID=255196)

### <a name="faq"></a>SSS
- [Kodlanmış UI testleri SSS-1](http://go.microsoft.com/fwlink/?LinkID=230576)

- [Kodlanmış UI testleri SSS-2](http://go.microsoft.com/fwlink/?LinkID=230578)

### <a name="forum"></a>Forum
- [Visual Studio UI Otomasyon testi (CodedUI içerir)](http://go.microsoft.com/fwlink/?LinkID=224497)

## <a name="see-also"></a>Ayrıca bkz.

- [UIMap](/previous-versions/dd580454(v=vs.140))
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>
- [Kod Kalitesini Geliştirme](https://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945)
- [İzlenecek yol: Kodlanmış Bir UI Testi Oluşturmak Düzenlemek ve Sürdürmek](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
- [Kodlanmış UI Testinin Anatomisi](../test/anatomy-of-a-coded-ui-test.md)
- [Kodlanmış UI Testleri için En İyi Yöntemler](../test/best-practices-for-coded-ui-tests.md)
- [Birden Çok UI Eşlemesi Bulunan Büyük Uygulamaları Sınama](../test/testing-a-large-application-with-multiple-ui-maps.md)
- [Kodlanmış UI Test Düzenleyicisi'ni Kullanarak Kodlanmış UI Testlerini Düzenleme](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md)
- [Kodlanmış UI Testleri ve Eylem Kayıtları için Desteklenen Yapılandırmalar ve Platformlar](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
- [Visual Studio 2010'dan Kodlanmış UI Testlerini Yükseltme](../test/upgrading-coded-ui-tests-from-visual-studio-2010.md)
- [Varolan bir eylem kaydından kodlanmış UI testi oluşturma](https://msdn.microsoft.com/library/56736963-9027-493b-b5c4-2d4e86d1d497)
