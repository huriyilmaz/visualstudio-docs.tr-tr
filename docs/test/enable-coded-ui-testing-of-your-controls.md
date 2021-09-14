---
title: Denetimlerinizin Kodlanmış UI Testlerini Etkinleştirme
description: Denetiminizi daha test edilebilir hale etmek için kodlanmış UI test çerçevesi desteği uygulama hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: d75e6debf4fb50be2d144f0843e6c0be6a84a76c
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628161"
---
# <a name="enable-coded-ui-testing-of-your-controls"></a>Denetimlerinizin kodlanmış UI testini etkinleştirme

Denetiminizi daha test edilebilir hale etmek için kodlanmış UI test çerçevesi için destek uygulama. Artımlı olarak artan destek düzeyleri ekleme. Kayıt ve kayıttan yürütme ile özellik doğrulamayı destekleerek başlayabilirsiniz. Ardından, kodlanmış UI test oluşturucus'un denetiminizin özel özelliklerini tanımasını sağlamak için bu özelliğin üzerine derlemeniz gerekir. Oluşturulan koddan bu özelliklere erişmek için özel sınıflar sağlama. Ayrıca, kodlanmış UI test oluşturucuslarının eylemleri kaydedilen eylemin amacına daha yakın bir şekilde yakalamasına da yardımcı olabilir.

! ChartControl'daki sınıfların CreateAccessabilityInstance sınıfı aracılığıyla ChartControlExtensionPackage'daki sınıflara nasıl genişletilişlerini gösteren diyagram.] (.. /test/media/cuit_full.png)

[!INCLUDE[coded-ui-test-deprecation](../test/includes/coded-ui-test-deprecation.md)]

## <a name="support-record-and-playback-and-property-validation-by-implementing-accessibility"></a>Erişilebilirlik gerçekleştirerek kayıttan yürütme ve özellik doğrulama desteği

Kodlanmış UI test oluşturucusu, kayıt sırasında karşılaştığı denetimlerle ilgili bilgileri yakalar ve ardından bu oturumu yeniden oynatmak için kod üretir. Denetiminiz erişilebilirliği desteklemezse, kodlanmış UI test oluşturucusu ekran koordinatlarını kullanarak eylemleri (fare tıklamaları gibi) yakalar. Test tekrar çalınca, oluşturulan kod eylemleri aynı ekran koordinatlarında görüntüler. Denetiminiz, test yeniden oynanarak ekranda farklı bir yerde görünürse, oluşturulan kod eylemi gerçekleştirene kadar başarısız olur. Denetiminiz için erişilebilirlik uygulamamasanız, test farklı ekran yapılandırmalarında, farklı ortamlarda veya kullanıcı arabirimi düzeni değiştinde yeniden çalınıyorsa test hataları görebilirsiniz.

![Kodlanmış KULLANıCı arabirimi test oluşturucusundaki kayıt penceresinin ekran görüntüsü. Duraklat düğmesi vurgulanmış ve araç ipucunda 'ChartControl' istemcisine tıklayın.](../test/media/cuit_recordnosupport.png)

Erişilebilirlik kullanırsanız, kodlanmış UI test oluşturucusu bunu bir testi kaydeden denetiminiz hakkında bilgi yakalamak için kullanır. Ardından, testi çalıştırarak oluşturulan kod, kullanıcı arabiriminde başka bir yerde olsa bile bu olayları denetiminize karşı yeniden oynatacak. Test yazarları denetiminizin temel özelliklerini kullanarak onaylar da oluşturabilir.

![Kodlanmış KULLANıCı arabirimi test oluşturucusundaki kayıt penceresinin ekran görüntüsü. Duraklat düğmesi vurgulanmış ve araç ipucunda 'A' etiketine tıklayın.](../test/media/cuit_record.png)

### <a name="to-support-record-and-playback-property-validation-and-navigation-for-a-windows-forms-control"></a>Windows Forms denetimi için kayıttan yürütme, özellik doğrulama ve gezintiyi desteklemek için
Aşağıdaki yordamda özetlenen ve içinde ayrıntılı olarak açıklanan şekilde denetiminiz için erişilebilirliği <xref:System.Windows.Forms.AccessibleObject> uygulama.

![CreateAccessabilityInstance ile ChartControl.CurveLegend sınıfı arasındaki ilişkiyi gösteren ChartControl sınıflarının diyagramı.](../test/media/cuit_accessible.png)

1. sınıfından türetilen bir sınıf <xref:System.Windows.Forms.Control.ControlAccessibleObject> uygulama ve <xref:System.Windows.Forms.Control.AccessibilityObject%2A> sınıfınıza bir nesnesi dönmek için özelliğini geçersiz kılın.

    ```csharp
    public partial class ChartControl : UserControl
    {
        // Overridden to return the custom AccessibleObject for the control.
        protected override AccessibleObject CreateAccessibilityInstance()
        {
            return new ChartControlAccessibleObject(this);
        }

        // Inner class ChartControlAccessibleObject represents accessible information
        // associated with the ChartControl and is used when recording tests.
        public class ChartControlAccessibleObject : ControlAccessibleObject
        {
            ChartControl myControl;
            public ChartControlAccessibleObject(ChartControl ctrl)
                : base(ctrl)
            {
                myControl = ctrl;
            }
        }
    }
    ```

2. Erişilebilir nesnenin , ve özelliklerini <xref:System.Windows.Forms.AccessibleObject.Role%2A> <xref:System.Windows.Forms.AccessibleObject.State%2A> ve yöntemlerini geçersiz <xref:System.Windows.Forms.AccessibleObject.GetChild%2A> <xref:System.Windows.Forms.AccessibleObject.GetChildCount%2A> kılın.

3. Alt denetim için başka bir erişilebilirlik nesnesi uygulama ve erişilebilirlik nesnesini geri dönmek <xref:System.Windows.Forms.Control.AccessibilityObject%2A> için alt denetimin özelliğini geçersiz kıl.

4. Alt <xref:System.Windows.Forms.AccessibleObject.Bounds%2A> denetimin erişilebilirlik nesnesi için , ve özelliklerini <xref:System.Windows.Forms.AccessibleObject.Name%2A> ve yöntemlerini geçersiz <xref:System.Windows.Forms.AccessibleObject.Parent%2A> <xref:System.Windows.Forms.AccessibleObject.Role%2A> <xref:System.Windows.Forms.AccessibleObject.State%2A> <xref:System.Windows.Forms.AccessibleObject.Navigate%2A> <xref:System.Windows.Forms.AccessibleObject.Select%2A> kılın.

> [!NOTE]
> Bu konu, içinde erişilebilirlik örneğiyle başlar <xref:System.Windows.Forms.AccessibleObject> ve ardından kalan yordamlarda bu örnek üzerinde derlemeler sağlar. Erişilebilirlik örneğinin çalışan bir sürümünü oluşturmak için bir konsol uygulaması oluşturun ve *program.cs'de* kodu örnek kodla değiştirin. Accessibility, System.Drawing ve System'e başvurular ekleyin. Windows. Forms. Derleme **uyarılarını ortadan kaldırmak için** Erişilebilirlik için Birlikte Çalışma Türlerini **Katıştırma** Yanlış olarak değiştirme. Uygulamayı çalıştırarak bir konsol **penceresinin** görünmesini **Windows için** projenin çıkış türünü Konsol Uygulaması'Windows Uygulaması olarak değiştirebilirsiniz.

## <a name="support-custom-property-validation-by-implementing-a-property-provider"></a>Özellik sağlayıcısını kullanarak özel özellik doğrulamayı destekleme

Kayıt ve kayıttan yürütme ve özellik doğrulama için temel desteği uygulamaya başladıktan sonra, eklentiyi kullanarak denetiminizin özel özelliklerini kodlanmış UI testlerinde <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> kullanılabilir hale geçirebilirsiniz. Örneğin, aşağıdaki yordam kodlanmış UI testlerinin grafik denetimi curveLegend alt denetimlerinin State özelliğine erişmesini sağlayan bir özellik sağlayıcısı oluşturur:

![Metin denetimi State özelliğinin seçili olduğu Onay Ekle penceresinin kısmen kapsıyor olduğu kodlanmış UI test oluşturucu ana penceresinin ekran görüntüsü.](../test/media/cuit_customprops.png)

### <a name="to-support-custom-property-validation"></a>Özel özellik doğrulamasını desteklemek için

![ChartControlextensionPackage ve ChartControlIPropertyProvider sınıflarının vurgulanmış olduğu ChartControl ve ChartControlExtension sınıflarının diyagramı.](../test/media/cuit_props.png)

1. Açıklama dizesinde zengin özellik değerlerini geçmek için eğri açıklaması erişilebilir <xref:System.Windows.Forms.AccessibleObject.Description%2A> nesnesinin özelliğini geçersiz kılın. Birden çok değeri noktalı virgülle ayırın (;).

    ```csharp
    public class CurveLegendAccessibleObject : AccessibleObject
    {
        // add the state property value to the description
        public override string Description
        {
            get
            {
                // Add ";" and the state value to the end
                // of the curve legend's description
                return "CurveLegend; " + State.ToString();
            }
        }
    }
    ```

1. Sınıf kitaplığı projesi oluşturarak denetiminiz için bir UI test uzantısı paketi oluşturun. Accessibility, Microsoft.VisualStudio.TestTools.UITesting, Microsoft.VisualStudio.TestTools.UITest.Common ve Microsoft.VisualStudio.TestTools.Extension'a başvurular ekleyin. Erişilebilirlik için **Birlikte Çalışma Türlerini Katıştırma'sini** False olarak **değiştirme.**

1. sınıfından türetilen bir özellik sağlayıcısı sınıfı <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> ekleyin:

    ```csharp
    using System;
    using System.Collections.Generic;
    using Accessibility;
    using Microsoft.VisualStudio.TestTools.UITesting;
    using Microsoft.VisualStudio.TestTools.UITest.Extension;
    using Microsoft.VisualStudio.TestTools.UITesting.WinControls;
    using Microsoft.VisualStudio.TestTools.UITest.Common;

    namespace ChartControlExtensionPackage
    {
        public class ChartControlPropertyProvider : UITestPropertyProvider
        {
        }
    }
    ```

1. Özellik adlarını ve özellik tanımlayıcılarını bir içine yerleştirerek özellik sağlayıcısını <xref:System.Collections.Generic.Dictionary%602> uygulama.

1. Derlemenizin <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetControlSupportLevel%2A?displayProperty=fullName> denetiminize ve onun üyelerine yönelik denetime özgü destek sağladığını belirtmek için geçersiz kılın.

1. 'nin kalan soyut yöntemlerini geçersiz kılın <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider?displayProperty=fullName>

1. 'den türetilen bir uzantı paketi sınıfı <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage> ekleyin.

1. Derleme `UITestExtensionPackage` için özniteliğini tanımlayın.

1. Uzantı paketi sınıfında, bir özellik <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A?displayProperty=fullName> sağlayıcısı isten geldiğinde özellik sağlayıcısı sınıfını geri dönmek için geçersiz kılın.

1. Kalan soyut yöntemleri ve özelliklerini geçersiz <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage> kılın.

1. Ikili dosyalarınızı derleme ve *%ProgramFiles%\Common\Microsoft Shared\VSTT\10.0\UITestExtensionPackages dizinine kopyalayın.*

> [!NOTE]
> Bu uzantı paketi, "Text" türünde herhangi bir denetime uygulanır. Aynı türde birden çok denetimi test ediyorsanız, testleri kaydı sırasında hangi uzantı paketlerinin dağıtılacağı yönetebilirsiniz.

## <a name="support-code-generation-by-implementing-a-class-to-access-custom-properties"></a>Özel özelliklere erişmek için bir sınıf uygulayarak kod oluşturma desteği

Kodlanmış UI test oluşturucusu bir oturum kaydından kod üretirken, denetimlerinize <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl> erişmek için sınıfını kullanır.

Denetiminizin özel özelliklerine erişim sağlamak için bir özellik sağlayıcısı uygulamaya aldıysanız, bu özelliklere erişmek için kullanılan özel bir sınıf abilirsiniz. Özelleştirilmiş bir sınıf eklemek, oluşturulan kodu basitleştiriyor.

### <a name="to-add-a-specialized-class-to-access-your-control"></a>Denetiminize erişmek için özelleştirilmiş bir sınıf eklemek için

![ChartControlExtensionPackage altında CurveLegend sınıfının vurgulanmış olduğu ChartControl ve ChartControlExtension sınıflarının diyagramı.](../test/media/cuit_codegen.png)

1. 'den türetilen bir sınıf <xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls.WinControl> uygulama ve denetimin türünü oluşturucuda arama özellikleri koleksiyonuna ekleyin.

1. Denetiminizin özel özelliklerini sınıfının özellikleri olarak uygulama.

1. Eğri gösterge alt denetimleri için <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetSpecializedClass%2A?displayProperty=fullName> yeni sınıfın türünü geri dönmek için özellik sağlayıcınızın yöntemini geçersiz kılın.

1. Yeni sınıfın <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetPropertyNamesClassType%2A> PropertyNames yönteminin türünü dönmek için özellik sağlayıcınızın yöntemini geçersiz kılın.

## <a name="support-intent-aware-actions-by-implementing-an-action-filter"></a>Eylem filtresi uygulayarak amace dikkati alan eylemleri destekleme

Test Visual Studio her fare ve klavye olayı yakalar. Ancak bazı durumlarda fare ve klavye olayları dizisinde eylemin amacı kaybolabilir. Örneğin, denetiminiz otomatik tamamlamayı destekliyorsa, test farklı bir ortamda yeniden oynanıyorsa aynı fare ve klavye olayları kümesi farklı bir değere neden olabilir. Klavye ve fare olaylarının dizisini tek bir eylemle değiştiren bir eylem filtresi eklentisi eklemek için kullanabilirsiniz. Bu şekilde, bir değeri seçen fare ve klavye olayları dizisini, değeri ayaran tek bir eylemle değiştirebilirsiniz. Bunu yapmak, kodlanmış UI testlerini bir ortamdan diğerine otomatik tamamlama farklarından korur.

### <a name="to-support-intent-aware-actions"></a>Amala ilgili eylemleri desteklemek için

![ChartControlExtensionPackage altında ChartControlActionFilter sınıfının vurgulanmış olduğu ChartControl ve ChartControlExtensionPackage sınıflarının diyagramı.](../test/media/cuit_actions.png)

1. [UITestActionFilter'dan](/previous-versions/visualstudio/visual-studio-2012/dd985757(v=vs.110))türetilen ve [ApplyTimeout](/previous-versions/visualstudio/visual-studio-2012/dd984649%28v%3dvs.110%29), [Category](/previous-versions/visualstudio/visual-studio-2012/dd986905(v=vs.110)), [Enabled](/previous-versions/visualstudio/visual-studio-2012/dd985633(v=vs.110)), [FilterType,](/previous-versions/visualstudio/visual-studio-2012/dd778726(v=vs.110)) [Group](/previous-versions/visualstudio/visual-studio-2012/dd779219(v=vs.110)) ve Name özelliklerini geçersiz karak bir eylem filtresi sınıfı [uygulama.](/previous-versions/visualstudio/visual-studio-2012/dd998334(v=vs.110))

1. [ProcessRule'i geçersiz kılın.](/previous-versions/visualstudio/visual-studio-2012/dd987281(v=vs.110)) Buradaki örnek, çift tıklama eylemlerini tek tıklamalı eylemle değiştirir.

1. Uzantı paketinizin <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A> yöntemine eylem filtresini ekleyin.

1. Ikili dosyalarınızı derleme ve *%ProgramFiles%\Common Files\Microsoft Shared\VSTT\10.0\UITestExtensionPackages dizinine kopyalayın.*

> [!NOTE]
> Eylem filtresi erişilebilirlik uygulamasına veya özellik sağlayıcısına bağlı değildir.

## <a name="debug-your-property-provider-or-action-filter"></a>Özellik sağlayıcınızda veya eylem filtrenizin hata ayıklaması

Özellik sağlayıcınız ve eylem filtreniz bir uzantı paketinde uygulanır. Test oluşturucusu uzantı paketini uygulamanıza ayrı bir işlemde çalıştırır.

### <a name="to-debug-your-property-provider-or-action-filter"></a>Özellik sağlayıcınızda veya eylem filtrenizin hata ayıklaması için

1. Uzantı paketinizin hata ayıklama sürümünü *derlemek için.dll* *ve .pdb* dosyalarını *%ProgramFiles%\Common Files\Microsoft Shared\VSTT\10.0\UITestExtensionPackages dizinine kopyalayın.*

2. Uygulamalarınızı çalıştırın (hata ayıklayıcıda değil).

3. Kodlanmış UI test oluşturucus nu çalıştırın.

     `codedUITestBuilder.exe  /standalone`

4. Hata ayıklayıcısını codedUITestBuilder sürecine ekleme.

5. Kodunda kesme noktaları ayarlayın.

6. Kodlanmış UI test oluşturucuda özellik sağlayıcınızı alıştırmak için onaylar oluşturun ve eylem filtrelerinizi alıştırmak için eylemleri kaydedin.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.AccessibleObject>
- [Kodunuzu test etmek için UI otomasyonunu kullanma](../test/use-ui-automation-to-test-your-code.md)
