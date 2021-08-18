---
title: Denetimlerinizin Kodlanmış UI Testlerini Etkinleştirme
description: Denetiminizi daha kararlı hale getirmek için kodlanmış UI test çerçevesi desteğinin nasıl uygulanacağını öğrenin.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122140043"
---
# <a name="enable-coded-ui-testing-of-your-controls"></a>Denetimlerinizin kodlanmış UI testlerini etkinleştirme

Denetiminizi daha kararlı hale getirmek için kodlanmış UI test çerçevesi için destek uygulayın. Artan destek düzeylerini artımlı olarak ekleyebilirsiniz. Kayıt ve kayıttan yürütme ve özellik doğrulamasını destekleyerek başlatın. Daha sonra, kodlanmış UI test oluşturucusunun denetiminizin özel özelliklerini tanımasını sağlamak için bunu oluşturun. Oluşturulan koddan Bu özelliklere erişmek için özel sınıflar sağlayın. Ayrıca, kodlanmış UI Test Oluşturucusu yakalama eylemlerine, kaydedilen eylemin amacına daha yakın bir şekilde de yardımcı olabilirsiniz.

! ChartControl içindeki sınıfların ChartControlExtensionPackage içindeki sınıflara Createaccessabilityınstance sınıfı aracılığıyla nasıl genişletilmişse gösteren diyagram.] (.. /test/Media/cuit_full.png)

[!INCLUDE[coded-ui-test-deprecation](../test/includes/coded-ui-test-deprecation.md)]

## <a name="support-record-and-playback-and-property-validation-by-implementing-accessibility"></a>Erişilebilirliği uygulayarak kaydı ve kayıttan yürütmeyi ve özellik doğrulamasını destekleme

Kodlanmış UI Test Oluşturucusu bir kayıt sırasında karşılaştığı denetimlerle ilgili bilgileri yakalar ve ardından bu oturumu yeniden oynatmak için kod üretir. Denetiminiz erişilebilirliği desteklemiyorsa, kodlanmış UI Test Oluşturucusu, ekran koordinatlarını kullanarak eylemleri (fare tıklamaları gibi) yakalar. Test kayıttan yürütüldüğünde, oluşturulan kod aynı Ekran koordinatlarındaki eylemleri yayınlar. Test kayıttan yürütüldüğünde denetiminiz ekran üzerinde farklı bir yerde görünürse, oluşturulan kod bu eylemi gerçekleştiremez. Denetiminiz için erişilebilirliği uygulamadığında, test, farklı ortamlarda veya Kullanıcı arabirimi düzeni değiştiğinde farklı ekran yapılandırmalarında kayıttan oynanabilir test hatalarıyla karşılaşabilirsiniz.

![Kodlanmış UI Test Oluşturucusu 'ndaki kayıt penceresinin ekran görüntüsü. Duraklat düğmesi vurgulanır ve araç ipucunda ' ChartControl ' istemcisi görüntülenir.](../test/media/cuit_recordnosupport.png)

Erişilebilirlik uygularsanız, kodlanmış UI Test Oluşturucusu bir testi kaydederken denetiminiz hakkındaki bilgileri yakalamak için bunu kullanır. Daha sonra, testi çalıştırdığınızda, Kullanıcı arabiriminde başka bir yerde olsa bile, oluşturulan kod bu olayları denetiinize karşı yeniden oynayacaktır. Test yazarları, denetiminizin temel özelliklerini kullanarak onaylar de oluşturabilir.

![Kodlanmış UI Test Oluşturucusu 'ndaki kayıt penceresinin ekran görüntüsü. Duraklat düğmesi vurgulanır ve araç ipucunda ' A ' etiketi görünür.](../test/media/cuit_record.png)

### <a name="to-support-record-and-playback-property-validation-and-navigation-for-a-windows-forms-control"></a>Windows Forms denetimine yönelik kayıt ve kayıttan yürütmeyi, özellik doğrulamayı ve gezintiyi desteklemek için
Aşağıdaki yordamda gösterildiği gibi denetiminiz için erişilebilirlik uygulayın ve ' de ayrıntılı olarak açıklanmıştır <xref:System.Windows.Forms.AccessibleObject> .

![Createaccessabilityınstance ve ChartControl. CurveLegend sınıfı arasındaki ilişkiyi gösteren ChartControl içindeki sınıfların diyagramı.](../test/media/cuit_accessible.png)

1. Sınıfından türetilen bir sınıf uygulayın <xref:System.Windows.Forms.Control.ControlAccessibleObject> ve <xref:System.Windows.Forms.Control.AccessibilityObject%2A> sınıfınızın bir nesnesini döndürmek için özelliği geçersiz kılın.

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

2. Erişilebilir nesnenin <xref:System.Windows.Forms.AccessibleObject.Role%2A> , <xref:System.Windows.Forms.AccessibleObject.State%2A> , <xref:System.Windows.Forms.AccessibleObject.GetChild%2A> ve <xref:System.Windows.Forms.AccessibleObject.GetChildCount%2A> özelliklerini ve yöntemlerini geçersiz kılın.

3. Alt denetim için başka bir erişilebilirlik nesnesi uygulayın ve <xref:System.Windows.Forms.Control.AccessibilityObject%2A> erişilebilirlik nesnesini döndürmek için alt denetimin özelliğini geçersiz kılın.

4. <xref:System.Windows.Forms.AccessibleObject.Bounds%2A> <xref:System.Windows.Forms.AccessibleObject.Name%2A> <xref:System.Windows.Forms.AccessibleObject.Parent%2A> <xref:System.Windows.Forms.AccessibleObject.Role%2A> <xref:System.Windows.Forms.AccessibleObject.State%2A> <xref:System.Windows.Forms.AccessibleObject.Navigate%2A> <xref:System.Windows.Forms.AccessibleObject.Select%2A> Alt denetimin erişilebilirlik nesnesi için,,,,,, ve özelliklerini ve yöntemlerini geçersiz kılın.

> [!NOTE]
> Bu konu, içindeki erişilebilirlik örneğiyle başlar <xref:System.Windows.Forms.AccessibleObject> ve ardından kalan yordamlarda Bu örnekte oluşturulur. Erişilebilirlik örneğinin çalışan bir sürümünü oluşturmak istiyorsanız, bir konsol uygulaması oluşturun ve ardından *program. cs* dosyasındaki kodu örnek kodla değiştirin. Erişilebilirlik, System. Drawing ve sistem 'e başvurular ekleyin. Windows. Formlarındaki. Bir yapı uyarısını ortadan kaldırmak için erişilebilirlik için **birlikte çalışma türlerini** **yanlış** olarak değiştirin. uygulamayı çalıştırdığınızda bir konsol penceresi görünmemesi için, projenin çıkış türünü **konsol uygulamasından** **Windows uygulamasına** dönüştürebilirsiniz.

## <a name="support-custom-property-validation-by-implementing-a-property-provider"></a>Özellik sağlayıcısı uygulayarak özel özellik doğrulamasını destekleme

Kayıt ve kayıttan yürütme ve Özellik doğrulama için temel desteği uyguladıktan sonra, bir eklenti uygulayarak denetiminizin özel özelliklerini kodlanmış UI testleri için kullanılabilir hale getirebilirsiniz <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> . Örneğin, aşağıdaki yordam, kodlanmış UI testlerinin grafik denetiminin CurveLegend alt denetimlerinin State özelliğine erişmesine izin veren bir özellik sağlayıcısı oluşturur:

![Kodlanmış UI Test Oluşturucusu ana penceresinin, bir metin denetiminin State özelliği olan bir onaylama ekleme penceresi tarafından kısmen ele alınan ekran görüntüsü.](../test/media/cuit_customprops.png)

### <a name="to-support-custom-property-validation"></a>Özel özellik doğrulamasını desteklemek için

![ChartControlExtensionPackage ve Chartcontrolıpropertyprovider sınıfları vurgulanmış şekilde ChartControl ve Chartcontrolexgerlein içindeki sınıfların diyagramı.](../test/media/cuit_props.png)

1. <xref:System.Windows.Forms.AccessibleObject.Description%2A>Açıklama dizesinde zengin özellik değerlerini geçirmek için eğri göstergesi erişilebilir nesnenin özelliğini geçersiz kılın. Birden çok değeri noktalı virgülle ayırın (;).

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

1. Bir sınıf kitaplığı projesi oluşturarak denetiminiz için bir UI test uzantısı paketi oluşturun. Erişilebilirlik, Microsoft. VisualStudio. TestTools. Uıitedıe, Microsoft. VisualStudio. TestTools. UITest. Common ve Microsoft. VisualStudio. TestTools. Extension 'a başvurular ekleyin. Erişilebilirlik için **Embed Interop türlerini** **false** olarak değiştirin.

1. Öğesinden türetilen bir özellik sağlayıcısı sınıfı ekleyin <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> :

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

1. Özellik adlarını ve özellik tanımlayıcılarını bir öğesine yerleştirerek Özellik sağlayıcısını uygulayın <xref:System.Collections.Generic.Dictionary%602> .

1. <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetControlSupportLevel%2A?displayProperty=fullName>Derlemelerinizin denetiminiz ve alt öğeleri için denetime özgü destek sağladığını belirtmek için geçersiz kılın.

1. Öğesinin kalan soyut yöntemlerini geçersiz kıl <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider?displayProperty=fullName>

1. Öğesinden türetilmiş bir uzantı paketi sınıfı ekleyin <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage> .

1. `UITestExtensionPackage`Derleme için özniteliği tanımlayın.

1. Uzantı paketi sınıfında, <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A?displayProperty=fullName> bir özellik sağlayıcısı istendiğinde özellik sağlayıcısı sınıfını döndürmek için geçersiz kılın.

1. Kalan soyut yöntemleri ve özelliklerini geçersiz kılın <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage> .

1. İkili dosyalarınızı derleyin ve *%ProgramFiles%\common\microsoft Shared\VSTT\10.0\UITestExtensionPackages* öğesine kopyalayın.

> [!NOTE]
> Bu uzantı paketi "metin" türünde herhangi bir denetime uygulanır. Aynı türden birden çok denetimi test ediyorsanız, testleri kaydettiğinizde hangi uzantı paketlerinin dağıtıldığını yönetebilmeniz için bunları ayrı olarak test edin.

## <a name="support-code-generation-by-implementing-a-class-to-access-custom-properties"></a>Özel özelliklere erişmek için bir sınıf uygulayarak kod oluşturmayı destekleme

Kodlanmış UI Test Oluşturucusu bir oturum kaydından kod oluşturduğunda, <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl> denetimlerinizi erişmek için sınıfını kullanır.

Denetiminizin özel özelliklerine erişim sağlamak için bir özellik sağlayıcısı uyguladıysanız, bu özelliklere erişmek için kullanılan özel bir sınıf ekleyebilirsiniz. Özelleştirilmiş bir sınıf eklemek oluşturulan kodu basitleştirir.

### <a name="to-add-a-specialized-class-to-access-your-control"></a>Denetime erişmek için özel bir sınıf eklemek için

![ChartControlExtensionPackage altında vurgulanmış olan CurveLegend sınıfı ile ChartControl ve Chartcontrolexlıve içindeki sınıfların diyagramı.](../test/media/cuit_codegen.png)

1. Öğesinden türetilmiş bir sınıf uygulayın <xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls.WinControl> ve denetimin türünü oluşturucuda arama özellikleri koleksiyonuna ekleyin.

1. Denetimin özel özelliklerini sınıfının özellikleri olarak uygulayın.

1. <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetSpecializedClass%2A?displayProperty=fullName>Eğri gösterge alt denetimleri için yeni sınıfın türünü döndürmek üzere özellik sağlayıcınızın yöntemini geçersiz kılın.

1. <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetPropertyNamesClassType%2A>Yeni sınıf ' PropertyNames yönteminin türünü döndürmek için özellik sağlayıcınızın metodunu geçersiz kılın.

## <a name="support-intent-aware-actions-by-implementing-an-action-filter"></a>Bir eylem filtresi uygulayarak amaç kullanan eylemleri destekleme

Visual Studio bir testi kaydeder, her fare ve klavye olayını yakalar. Ancak bazı durumlarda, eylemin amacı fare ve klavye olayları dizisinde kaybolabilir. Örneğin, denetiminiz otomatik tamamlamayı destekliyorsa, test farklı bir ortamda kayıttan yürütüldüğünde aynı fare ve klavye olayları kümesi farklı bir değer oluşmasına neden olabilir. Klavye ve fare olaylarının serisini tek bir eylemle değiştiren bir eylem filtresi eklentisi ekleyebilirsiniz. Bu şekilde, değeri ayarlayan tek bir eylemle bir değer seçerek fare ve klavye olaylarının serisini değiştirebilirsiniz. Bunun yapılması, kodlanmış UI testlerini bir ortamdan diğerine AutoComplete 'teki farklılıklardan korur.

### <a name="to-support-intent-aware-actions"></a>Amaç kullanan eylemleri desteklemek için

![ChartControlExtensionPackage altında vurgulanmış Chartcontrollactionfilter sınıfıyla birlikte ChartControl ve ChartControlExtensionPackage sınıflarının diyagramı.](../test/media/cuit_actions.png)

1. [Uitestactionfilter](/previous-versions/visualstudio/visual-studio-2012/dd985757(v=vs.110))öğesinden türetilmiş bir eylem filtresi sınıfı uygulayıp [ApplyTimeout](/previous-versions/visualstudio/visual-studio-2012/dd984649%28v%3dvs.110%29), [Kategori](/previous-versions/visualstudio/visual-studio-2012/dd986905(v=vs.110)), [etkin](/previous-versions/visualstudio/visual-studio-2012/dd985633(v=vs.110)), [FilterType](/previous-versions/visualstudio/visual-studio-2012/dd778726(v=vs.110)), [Grup](/previous-versions/visualstudio/visual-studio-2012/dd779219(v=vs.110)) ve [ad](/previous-versions/visualstudio/visual-studio-2012/dd998334(v=vs.110))özelliklerini geçersiz kılar.

1. [ProcessRule](/previous-versions/visualstudio/visual-studio-2012/dd987281(v=vs.110))öğesini geçersiz kılın. Buradaki örnek, tek tıklamayla bir eylemle birlikte çift tıklama eylemini değiştirir.

1. Eylem filtresini <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A> uzantı paketinizin yöntemine ekleyin.

1. İkili dosyalarınızı derleyin ve *%ProgramFiles%\Common Files\Microsoft Shared\VSTT\10.0\UITestExtensionPackages* öğesine kopyalayın.

> [!NOTE]
> Eylem filtresi, erişilebilirlik uygulamasına veya özellik sağlayıcısına bağlı değildir.

## <a name="debug-your-property-provider-or-action-filter"></a>Özellik sağlayıcınızda veya eylem süzgecinde hata ayıklayın

Özellik sağlayıcınız ve eylem filtreniz bir uzantı paketinde uygulanır. Test Oluşturucusu, uzantı paketini uygulamanızdan ayrı bir işlemde çalıştırır.

### <a name="to-debug-your-property-provider-or-action-filter"></a>Özellik sağlayıcınızdaki veya eylem filtreinizdeki hataları ayıklamak için

1. Uzantı paketinizin hata ayıklama sürümünü oluşturun *.dll* ve *. pdb* dosyalarını *%ProgramFiles%\Common Files\Microsoft Shared\VSTT\10.0\UITestExtensionPackages* klasörüne kopyalayın.

2. Uygulamanızı çalıştırın (hata ayıklayıcıda değil).

3. Kodlanmış UI test oluşturucuyu çalıştırın.

     `codedUITestBuilder.exe  /standalone`

4. Hata ayıklayıcıyı codedUITestBuilder işlemine iliştirin.

5. Kodunuzda kesme noktaları ayarlayın.

6. Kodlanmış UI Test Oluşturucusu ' nda, özellik sağlayıcınızı alıştırmaya yönelik onaylar oluşturun ve eylem filtrelerinizi uygulamak için eylemleri kaydedin.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.AccessibleObject>
- [Kodunuzu test etmek için UI Otomasyonunu kullanma](../test/use-ui-automation-to-test-your-code.md)
