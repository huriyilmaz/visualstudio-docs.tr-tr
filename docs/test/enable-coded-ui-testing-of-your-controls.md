---
title: Denetimlerinizin Kodlanmış UI Testlerini Etkinleştirme
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: feb7785678be4b6f2c26bbcff93bf7d3e6632116
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589623"
---
# <a name="enable-coded-ui-testing-of-your-controls"></a>Denetimlerinizin kodlanmış UI testlerini etkinleştirme

Denetiminizi daha kararlı hale getirmek için kodlanmış UI test çerçevesi için destek uygulayın. Artan destek düzeylerini artımlı olarak ekleyebilirsiniz. Kayıt ve kayıttan yürütme ve özellik doğrulamasını destekleyerek başlatın. Daha sonra, kodlanmış UI test oluşturucusunun denetiminizin özel özelliklerini tanımasını sağlamak için bunu oluşturun. Oluşturulan koddan Bu özelliklere erişmek için özel sınıflar sağlayın. Ayrıca, kodlanmış UI Test Oluşturucusu yakalama eylemlerine, kaydedilen eylemin amacına daha yakın bir şekilde de yardımcı olabilirsiniz.

![CUIT&#95;tam](../test/media/cuit_full.png)

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="support-record-and-playback-and-property-validation-by-implementing-accessibility"></a>Erişilebilirliği uygulayarak kaydı ve kayıttan yürütmeyi ve özellik doğrulamasını destekleme

Kodlanmış UI Test Oluşturucusu bir kayıt sırasında karşılaştığı denetimlerle ilgili bilgileri yakalar ve ardından bu oturumu yeniden oynatmak için kod üretir. Denetiminiz erişilebilirliği desteklemiyorsa, kodlanmış UI Test Oluşturucusu, ekran koordinatlarını kullanarak eylemleri (fare tıklamaları gibi) yakalar. Test kayıttan yürütüldüğünde, oluşturulan kod aynı Ekran koordinatlarındaki eylemleri yayınlar. Test kayıttan yürütüldüğünde denetiminiz ekran üzerinde farklı bir yerde görünürse, oluşturulan kod bu eylemi gerçekleştiremez. Denetiminiz için erişilebilirliği uygulamadığında, test, farklı ortamlarda veya Kullanıcı arabirimi düzeni değiştiğinde farklı ekran yapılandırmalarında kayıttan oynanabilir test hatalarıyla karşılaşabilirsiniz.

![CUıT&#95;recordnosupport](../test/media/cuit_recordnosupport.png)

Erişilebilirlik uygularsanız, kodlanmış UI Test Oluşturucusu bir testi kaydederken denetiminiz hakkındaki bilgileri yakalamak için bunu kullanır. Daha sonra, testi çalıştırdığınızda, Kullanıcı arabiriminde başka bir yerde olsa bile, oluşturulan kod bu olayları denetiinize karşı yeniden oynayacaktır. Test yazarları, denetiminizin temel özelliklerini kullanarak onaylar de oluşturabilir.

![CUIT&#95;kaydı](../test/media/cuit_record.png)

### <a name="to-support-record-and-playback-property-validation-and-navigation-for-a-windows-forms-control"></a>Windows Forms denetimine yönelik kayıt ve kayıttan yürütmeyi, özellik doğrulamayı ve gezintiyi desteklemek için
Aşağıdaki yordamda gösterildiği gibi denetiminiz için erişilebilirlik uygulayın ve <xref:System.Windows.Forms.AccessibleObject>ayrıntılı olarak açıklanmıştır.

![Erişilebilir CUıT&#95;](../test/media/cuit_accessible.png)

1. <xref:System.Windows.Forms.Control.ControlAccessibleObject>türeten bir sınıf uygulayın ve sınıfınızın bir nesnesini döndürmek için <xref:System.Windows.Forms.Control.AccessibilityObject%2A> özelliğini geçersiz kılın.

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

2. Erişilebilir nesnenin <xref:System.Windows.Forms.AccessibleObject.Role%2A>, <xref:System.Windows.Forms.AccessibleObject.State%2A>, <xref:System.Windows.Forms.AccessibleObject.GetChild%2A> ve <xref:System.Windows.Forms.AccessibleObject.GetChildCount%2A> özelliklerini ve yöntemlerini geçersiz kılın.

3. Alt denetim için başka bir erişilebilirlik nesnesi uygulayın ve erişilebilirlik nesnesini döndürmek için alt denetimin <xref:System.Windows.Forms.Control.AccessibilityObject%2A> özelliğini geçersiz kılın.

4. Alt denetimin erişilebilirlik nesnesi için <xref:System.Windows.Forms.AccessibleObject.Bounds%2A>, <xref:System.Windows.Forms.AccessibleObject.Name%2A>, <xref:System.Windows.Forms.AccessibleObject.Parent%2A>, <xref:System.Windows.Forms.AccessibleObject.Role%2A>, <xref:System.Windows.Forms.AccessibleObject.State%2A>, <xref:System.Windows.Forms.AccessibleObject.Navigate%2A>ve <xref:System.Windows.Forms.AccessibleObject.Select%2A> özelliklerini ve yöntemlerini geçersiz kılın.

> [!NOTE]
> Bu konu, <xref:System.Windows.Forms.AccessibleObject>erişilebilirlik örneğiyle başlar ve ardından kalan yordamlarda Bu örnekte oluşturulur. Erişilebilirlik örneğinin çalışan bir sürümünü oluşturmak istiyorsanız, bir konsol uygulaması oluşturun ve *program.cs* içindeki kodu örnek kodla değiştirin. Erişilebilirlik, System. Drawing ve System. Windows. Forms 'a başvurular ekleyin. Bir yapı uyarısını ortadan kaldırmak için erişilebilirlik için **birlikte çalışma türlerini** **yanlış** olarak değiştirin. Uygulamanın çıkış türünü **konsol** uygulamasından **Windows uygulamasına** değiştirerek, uygulamayı çalıştırdığınızda bir konsol penceresinin görünmesini sağlayabilirsiniz.

## <a name="support-custom-property-validation-by-implementing-a-property-provider"></a>Özellik sağlayıcısı uygulayarak özel özellik doğrulamasını destekleme

Kayıt ve kayıttan yürütme ve Özellik doğrulama için temel desteği uyguladıktan sonra, bir <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> eklentisi uygulayarak, denetimin özel özelliklerini kodlanmış UI testleri için kullanılabilir hale getirebilirsiniz. Örneğin, aşağıdaki yordam, kodlanmış UI testlerinin grafik denetiminin CurveLegend alt denetimlerinin State özelliğine erişmesine izin veren bir özellik sağlayıcısı oluşturur:

![CUIT&#95;customprops](../test/media/cuit_customprops.png)

### <a name="to-support-custom-property-validation"></a>Özel özellik doğrulamasını desteklemek için

![CUıT&#95;props](../test/media/cuit_props.png)

1. Açıklama dizesinde zengin özellik değerlerini geçirmek için eğri göstergesi erişilebilir nesnenin <xref:System.Windows.Forms.AccessibleObject.Description%2A> özelliğini geçersiz kılın. Birden çok değeri noktalı virgülle ayırın (;).

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

1. Bir sınıf kitaplığı projesi oluşturarak denetiminiz için bir UI test uzantısı paketi oluşturun. Erişilebilirlik, Microsoft. VisualStudio. TestTools. Uıitedıe, Microsoft. VisualStudio. TestTools. UITest. Common ve Microsoft. VisualStudio. TestTools. Extension 'a başvurular ekleyin. Erişilebilirlik için **Embed Interop türlerini** **false**olarak değiştirin.

1. <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>türetilmiş bir özellik sağlayıcısı sınıfı ekleyin:

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

1. Özellik adlarını ve özellik tanımlayıcılarını bir <xref:System.Collections.Generic.Dictionary%602>yerleştirerek Özellik sağlayıcısını uygulayın.

1. Derlemenizi, denetiminiz ve alt öğeleri için denetime özgü destek sağladığını göstermek için <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetControlSupportLevel%2A?displayProperty=fullName> geçersiz kılın.

1. <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider?displayProperty=fullName> kalan soyut yöntemlerini geçersiz kılın

1. <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>türetilmiş bir uzantı paketi sınıfı ekleyin.

1. Derleme için `UITestExtensionPackage` özniteliğini tanımlayın.

1. Uzantı paketi sınıfında, bir özellik sağlayıcısı istendiğinde, özellik sağlayıcısı sınıfını döndürmek için <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A?displayProperty=fullName> geçersiz kılın.

1. <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>kalan soyut yöntemleri ve özellikleri geçersiz kılın.

1. İkili dosyalarınızı derleyin ve *%ProgramFiles%\common\microsoft Shared\VSTT\10.0\UITestExtensionPackages*öğesine kopyalayın.

> [!NOTE]
> Bu uzantı paketi "metin" türünde herhangi bir denetime uygulanır. Aynı türden birden çok denetimi test ediyorsanız, testleri kaydettiğinizde hangi uzantı paketlerinin dağıtıldığını yönetebilmeniz için bunları ayrı olarak test edin.

## <a name="support-code-generation-by-implementing-a-class-to-access-custom-properties"></a>Özel özelliklere erişmek için bir sınıf uygulayarak kod oluşturmayı destekleme

Kodlanmış UI Test Oluşturucusu bir oturum kaydından kod oluşturduğunda, denetimleriniz erişmek için <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl> sınıfını kullanır.

Denetiminizin özel özelliklerine erişim sağlamak için bir özellik sağlayıcısı uyguladıysanız, bu özelliklere erişmek için kullanılan özel bir sınıf ekleyebilirsiniz. Özelleştirilmiş bir sınıf eklemek oluşturulan kodu basitleştirir.

### <a name="to-add-a-specialized-class-to-access-your-control"></a>Denetime erişmek için özel bir sınıf eklemek için

![CUıT&#95;CodeGen](../test/media/cuit_codegen.png)

1. <xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls.WinControl> türetilen bir sınıf uygulayın ve denetimin türünü oluşturucuda arama özellikleri koleksiyonuna ekleyin.

1. Denetimin özel özelliklerini sınıfının özellikleri olarak uygulayın.

1. Eğri gösterge alt denetimleri için yeni sınıfın türünü döndürmek üzere özellik sağlayıcınızın <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetSpecializedClass%2A?displayProperty=fullName> yöntemini geçersiz kılın.

1. Yeni sınıf ' PropertyNames yönteminin türünü döndürmek için özellik sağlayıcınızın <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetPropertyNamesClassType%2A> yöntemini geçersiz kılın.

## <a name="support-intent-aware-actions-by-implementing-an-action-filter"></a>Bir eylem filtresi uygulayarak amaç kullanan eylemleri destekleme

Visual Studio bir testi kaydeder, her fare ve klavye olayını yakalar. Ancak bazı durumlarda, eylemin amacı fare ve klavye olayları dizisinde kaybolabilir. Örneğin, denetiminiz otomatik tamamlamayı destekliyorsa, test farklı bir ortamda kayıttan yürütüldüğünde aynı fare ve klavye olayları kümesi farklı bir değer oluşmasına neden olabilir. Klavye ve fare olaylarının serisini tek bir eylemle değiştiren bir eylem filtresi eklentisi ekleyebilirsiniz. Bu şekilde, değeri ayarlayan tek bir eylemle bir değer seçerek fare ve klavye olaylarının serisini değiştirebilirsiniz. Bunun yapılması, kodlanmış UI testlerini bir ortamdan diğerine AutoComplete 'teki farklılıklardan korur.

### <a name="to-support-intent-aware-actions"></a>Amaç kullanan eylemleri desteklemek için

![CUıT&#95;eylemleri](../test/media/cuit_actions.png)

1. [Uitestactionfilter](/previous-versions/visualstudio/visual-studio-2012/dd985757(v=vs.110))öğesinden türetilmiş bir eylem filtresi sınıfı uygulayıp [ApplyTimeout](/previous-versions/visualstudio/visual-studio-2012/dd984649%28v%3dvs.110%29), [Kategori](/previous-versions/visualstudio/visual-studio-2012/dd986905(v=vs.110)), [etkin](/previous-versions/visualstudio/visual-studio-2012/dd985633(v=vs.110)), [FilterType](/previous-versions/visualstudio/visual-studio-2012/dd778726(v=vs.110)), [Grup](/previous-versions/visualstudio/visual-studio-2012/dd779219(v=vs.110)) ve [ad](/previous-versions/visualstudio/visual-studio-2012/dd998334(v=vs.110))özelliklerini geçersiz kılar.

1. [ProcessRule](/previous-versions/visualstudio/visual-studio-2012/dd987281(v=vs.110))öğesini geçersiz kılın. Buradaki örnek, tek tıklamayla bir eylemle birlikte çift tıklama eylemini değiştirir.

1. Eylem filtresini uzantı paketinizin <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A> yöntemine ekleyin.

1. İkili dosyalarınızı derleyin ve *%ProgramFiles%\Common Files\Microsoft Shared\VSTT\10.0\UITestExtensionPackages*öğesine kopyalayın.

> [!NOTE]
> Eylem filtresi, erişilebilirlik uygulamasına veya özellik sağlayıcısına bağlı değildir.

## <a name="debug-your-property-provider-or-action-filter"></a>Özellik sağlayıcınızda veya eylem süzgecinde hata ayıklayın

Özellik sağlayıcınız ve eylem filtreniz bir uzantı paketinde uygulanır. Test Oluşturucusu, uzantı paketini uygulamanızdan ayrı bir işlemde çalıştırır.

### <a name="to-debug-your-property-provider-or-action-filter"></a>Özellik sağlayıcınızdaki veya eylem filtreinizdeki hataları ayıklamak için

1. Uzantı paketinizin hata ayıklama sürümünü oluşturun *. dll* ve *. pdb* dosyalarını *%ProgramFiles%\Common Files\Microsoft Shared\VSTT\10.0\UITestExtensionPackages*klasörüne kopyalayın.

2. Uygulamanızı çalıştırın (hata ayıklayıcıda değil).

3. Kodlanmış UI test oluşturucuyu çalıştırın.

     `codedUITestBuilder.exe  /standalone`

4. Hata ayıklayıcıyı codedUITestBuilder işlemine iliştirin.

5. Kodunuzda kesme noktaları ayarlayın.

6. Kodlanmış UI Test Oluşturucusu ' nda, özellik sağlayıcınızı alıştırmaya yönelik onaylar oluşturun ve eylem filtrelerinizi uygulamak için eylemleri kaydedin.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.AccessibleObject>
- [UI otomasyonunu kullanarak kodunuzu test etme](../test/use-ui-automation-to-test-your-code.md)
