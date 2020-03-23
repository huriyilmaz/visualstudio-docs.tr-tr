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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589623"
---
# <a name="enable-coded-ui-testing-of-your-controls"></a>Denetimlerinizin kodlanmış UI testini etkinleştirme

Denetiminizi daha sınanabilir hale getirmek için kodlanmış UI test çerçevesi için destek uygulayın. Artan destek düzeylerini artımlı olarak ekleyebilirsiniz. Kayıt ve oynatma ve özellik doğrulaması destekleyerek başlayın. Ardından, kodlanmış Kullanıcı Bira Testi oluşturucunun denetiminizin özel özelliklerini tanımasını sağlamak için bunun üzerine inşa edin. Oluşturulan koddan bu özelliklere erişmek için özel sınıflar sağlayın. Ayrıca, kodlanmış UI test oluşturucusu, kaydedilen eylemin amacına daha yakın bir şekilde eylemleri yakalamasına da yardımcı olabilirsiniz.

![CUIT&#95;Tam](../test/media/cuit_full.png)

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="support-record-and-playback-and-property-validation-by-implementing-accessibility"></a>Erişilebilirlik uygulayarak kayıt ve oynatma ve özellik doğrulaması desteği

Kodlanmış Kullanıcı Altı Bilgi düzeyi test oluşturucusu, bir kayıt sırasında karşılaştığı denetimler hakkında bilgi yakalar ve ardından bu oturumu yeniden oynatmak için kod oluşturur. Denetiminiz erişilebilirliği desteklemiyorsa, kodlanmış UI test oluşturucusu ekran koordinatlarını kullanarak eylemleri (fare tıklamaları gibi) yakalar. Test oynatıldığında, oluşturulan kod eylemleri aynı ekran koordinatlarında yayınlar. Denetiminiz test oynatıldığında ekranda farklı bir yerde görünürse, oluşturulan kod eylemi gerçekleştiremezse. Denetiminiz için erişilebilirliği uygulamayarak, test farklı ekran yapılandırmalarında, farklı ortamlarda veya UI düzeni değiştiğinde oynatılırsa test hataları görebilirsiniz.

![CUIT&#95;RecordNoSupport](../test/media/cuit_recordnosupport.png)

Erişilebilirlik uygularsanız, kodlanmış Kullanıcı Bira test oluşturucusu, bir testi kaydederken denetiminiz hakkındaki bilgileri yakalamak için kullanır. Daha sonra, testi çalıştırdığınızda, oluşturulan kod, kullanıcı arabiriminde başka bir yerde olsa bile bu olayları denetiminize karşı yeniden yürütecektir. Test yazarları, denetiminizin temel özelliklerini kullanarak ileri makaleler de oluşturabilir.

![CUIT&#95;Kaydı](../test/media/cuit_record.png)

### <a name="to-support-record-and-playback-property-validation-and-navigation-for-a-windows-forms-control"></a>Windows Forms denetimi için kayıt ve oynatmayı, özellik doğrulamayı ve gezinmeyi desteklemek için
Aşağıdaki yordamda belirtildiği gibi denetiminiz için erişilebilirliği uygulayın <xref:System.Windows.Forms.AccessibleObject>ve ayrıntılı olarak açıklanmıştır.

![CUIT&#95;Erişilebilir](../test/media/cuit_accessible.png)

1. Sınıfınızın bir nesnesini <xref:System.Windows.Forms.Control.ControlAccessibleObject>döndürmek için özelliği <xref:System.Windows.Forms.Control.AccessibilityObject%2A> türeten bir sınıf uygulayın ve özelliği geçersiz kılın.

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

2. Erişilebilir <xref:System.Windows.Forms.AccessibleObject.Role%2A>nesnenin , , <xref:System.Windows.Forms.AccessibleObject.State%2A> <xref:System.Windows.Forms.AccessibleObject.GetChild%2A> ve <xref:System.Windows.Forms.AccessibleObject.GetChildCount%2A> özellikleri ve yöntemleri geçersiz kılın.

3. Alt denetim için başka bir erişilebilirlik nesnesi uygulayın ve erişilebilirlik nesnesini döndürmek için alt denetimin <xref:System.Windows.Forms.Control.AccessibilityObject%2A> özelliğini geçersiz kılın.

4. Alt denetimin <xref:System.Windows.Forms.AccessibleObject.Name%2A> <xref:System.Windows.Forms.AccessibleObject.Parent%2A>erişilebilirlik <xref:System.Windows.Forms.AccessibleObject.Navigate%2A>nesnesi <xref:System.Windows.Forms.AccessibleObject.Bounds%2A>için <xref:System.Windows.Forms.AccessibleObject.Select%2A> , , <xref:System.Windows.Forms.AccessibleObject.Role%2A> <xref:System.Windows.Forms.AccessibleObject.State%2A>, , , ve özelliklerini ve yöntemleri geçersiz kılın.

> [!NOTE]
> Bu konu, 'deki <xref:System.Windows.Forms.AccessibleObject>erişilebilirlik örneğiyle başlar ve sonra kalan yordamlarda bu örnek üzerine oluşturur. Erişilebilirlik örneğinin çalışan bir sürümünü oluşturmak istiyorsanız, bir konsol uygulaması oluşturun ve *ardından Program.cs* kodu örnek kodla değiştirin. Erişilebilirlik, System.Drawing ve System.Windows.Forms'a göndermeler ekleyin. Yapı uyarısını ortadan kaldırmak için Accessibilite için **Embed Interop Türlerini** **False'a** değiştirin. Uygulamayı çalıştırdığınızda konsol penceresinin görünmemesi için projenin çıktı türünü **Konsol Uygulaması'ndan** **Windows Uygulaması'na** değiştirebilirsiniz.

## <a name="support-custom-property-validation-by-implementing-a-property-provider"></a>Bir özellik sağlayıcısı uygulayarak özel özellik doğrulamayı destekleme

Kayıt ve kayıt ve özellik doğrulama için temel desteği uyguladıktan sonra, bir <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> eklenti uygulayarak denetiminizin özel özelliklerini kodlanmış Kullanıcı Arabirimi testleri için kullanılabilir hale getirebilirsiniz. Örneğin, aşağıdaki yordam, kodlanmış Kullanıcı Arabirimi testlerinin grafik denetiminin CurveLegend alt denetimlerinin Devlet özelliğine erişmesine izin veren bir özellik sağlayıcısı oluşturur:

![CUIT&#95;CustomProps](../test/media/cuit_customprops.png)

### <a name="to-support-custom-property-validation"></a>Özel özellik doğrulaması desteklemek için

![CUIT&#95;Sahne](../test/media/cuit_props.png)

1. Açıklama dizesinde zengin özellik <xref:System.Windows.Forms.AccessibleObject.Description%2A> değerlerini geçirmek için eğri göstergesi erişilebilir nesnenin özelliğigeçersiz. Birden çok değeri yarı iki nokta üst üste (;).

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

1. Sınıf kitaplığı projesi oluşturarak denetiminiz için bir UI test uzantısı paketi oluşturun. Erişilebilirlik, Microsoft.VisualStudio.TestTools.UITesting, Microsoft.VisualStudio.TestTools.UITest.Common ve Microsoft.VisualStudio.TestTools.Extension başvuruları ekleyin. Accessibility için **Embed Interop Türlerini** **False'a**değiştirin.

1. <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>Türetilen bir özellik sağlayıcı sınıfı ekleyin:

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

1. Özellik adlarını ve özellik tanımlayıcılarını bir <xref:System.Collections.Generic.Dictionary%602>'ye yerleştirerek özellik sağlayıcısını uygulayın.

1. Derlemenizin denetiminiz ve alt ları için denetime özel destek sağladığını belirtmek için geçersiz kılın. <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetControlSupportLevel%2A?displayProperty=fullName>

1. Kalan soyut yöntemleri geçersiz kılmak<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider?displayProperty=fullName>

1. 'den <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>türetilen bir uzantı paketi sınıfı ekleyin.

1. `UITestExtensionPackage` Derleme için özniteliği tanımlayın.

1. Uzantı paketi sınıfında, <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A?displayProperty=fullName> bir özellik sağlayıcısı istendiğinde özellik sağlayıcı sınıfını döndürmek için geçersiz kılın.

1. <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>Kalan soyut yöntemleri ve özelliklerini geçersiz kılın.

1. İkililerinizi oluşturun ve *%ProgramFiles%\Common\Microsoft Shared\VSTT\10.0\UITestExtensionPackages'a*kopyalayın.

> [!NOTE]
> Bu uzantı paketi "Metin" türünden herhangi bir denetime uygulanır. Aynı türde birden çok denetimse, testleri kaydederken hangi uzantı paketlerinin dağıtıldığına göre bunları ayrı ayrı test edin.

## <a name="support-code-generation-by-implementing-a-class-to-access-custom-properties"></a>Özel özelliklere erişmek için bir sınıf uygulayarak kod oluşturmayı destekleyin

Kodlanmış UI test oluşturucusu bir oturum kaydından <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl> kod oluşturduğunda, denetimlerinize erişmek için sınıfı kullanır.

Denetiminizin özel özelliklerine erişim sağlamak için bir özellik sağlayıcısı uyguladıysanız, bu özelliklere erişmek için kullanılan özel bir sınıf ekleyebilirsiniz. Özelleştirilmiş bir sınıf eklemek, oluşturulan kodu basitleştirir.

### <a name="to-add-a-specialized-class-to-access-your-control"></a>Denetiminize erişmek için özel bir sınıf eklemek için

![CUIT&#95;CodeGen](../test/media/cuit_codegen.png)

1. Yapı oluşturucudaki arama <xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls.WinControl> özellikleri koleksiyonundan türetilen bir sınıf uygulayın ve denetimin türünü ekleyin.

1. Denetiminizin özel özelliklerini sınıfın özellikleri olarak uygulayın.

1. Eğri gösterge alt denetimleri için yeni sınıfın türünü döndürmek için mülk sağlayıcınızın <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetSpecializedClass%2A?displayProperty=fullName> yöntemini geçersiz kılın.

1. Yeni sınıfın Özellik Adları <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetPropertyNamesClassType%2A> yönteminin türünü döndürmek için mülk sağlayıcınızın yöntemini geçersiz kılın.

## <a name="support-intent-aware-actions-by-implementing-an-action-filter"></a>Eylem filtresi uygulayarak niyete duyarlı eylemleri destekleme

Visual Studio bir testi kaydettiğinde, her fare ve klavye olayını yakalar. Ancak, bazı durumlarda, eylemin amacı fare ve klavye olayları serisinde kaybolabilir. Örneğin, denetiminiz otomatik tamamlamayı destekliyorsa, test farklı bir ortamda oynatıldığında aynı fare ve klavye olayları kümesi farklı bir değere neden olabilir. Klavye ve fare olayları serisinin yerine tek bir eylemle gelen bir eylem filtresi eklentisi ekleyebilirsiniz. Bu şekilde, değeri ayarlayan tek bir eylemle bir değer seçen fare ve klavye olayları serisini değiştirebilirsiniz. Bunu yapmak, kodlanmış UI testlerini bir ortamdan diğerine otomatik tamamlama farklılıklarından korur.

### <a name="to-support-intent-aware-actions"></a>Niyete duyarlı eylemleri desteklemek için

![CUIT&#95;Eylemler](../test/media/cuit_actions.png)

1. [UITestActionFilter](/previous-versions/visualstudio/visual-studio-2012/dd985757(v=vs.110))türetilen bir eylem filtresi sınıfı uygulayın , [özellikleri Geçersiz UygulamaTimeout](/previous-versions/visualstudio/visual-studio-2012/dd984649%28v%3dvs.110%29), [Kategori](/previous-versions/visualstudio/visual-studio-2012/dd986905(v=vs.110)), [Etkin](/previous-versions/visualstudio/visual-studio-2012/dd985633(v=vs.110)), [FilterType](/previous-versions/visualstudio/visual-studio-2012/dd778726(v=vs.110)), [Grup](/previous-versions/visualstudio/visual-studio-2012/dd779219(v=vs.110)) ve [Ad](/previous-versions/visualstudio/visual-studio-2012/dd998334(v=vs.110)).

1. [ProcessRule](/previous-versions/visualstudio/visual-studio-2012/dd987281(v=vs.110))geçersiz kılın. Buradaki örnek, çift tıklatma eylemini tek tıklatma eylemiyle değiştirir.

1. Eylem filtresini uzantı paketinizin yöntemine <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A> ekleyin.

1. İkililerinizi oluşturun ve *%ProgramFiles%\Common Files\Microsoft Shared\VSTT\10.0\UITestExtensionPackages'* a kopyalayın.

> [!NOTE]
> Eylem filtresi erişilebilirlik uygulamasına veya özellik sağlayıcısına bağlı değildir.

## <a name="debug-your-property-provider-or-action-filter"></a>Mülk sağlayıcınızı veya eylem filtrenizi hata ayıklama

Özellik sağlayıcınız ve eylem filtreniz bir uzantı paketinde uygulanır. Test oluşturucu, uzantı paketini uygulamanızdan ayrı bir işlemle çalıştırAr.

### <a name="to-debug-your-property-provider-or-action-filter"></a>Mülk sağlayıcınızı veya eylem filtrenizi hata ayıklamak için

1. Uzantı paketinizin hata ayıklama sürümünü oluşturun *.dll* ve *.pdb* dosyalarını *%ProgramFiles%\Common Files\Microsoft Shared\VSTT\10.0\UITestExtensionPackages'a*kopyalayın.

2. Uygulamanızı çalıştırın (hata ayıklamada değil).

3. Kodlanmış UI test oluşturucuyu çalıştırın.

     `codedUITestBuilder.exe  /standalone`

4. KodlanmışUITestBuilder işlemine hata ayıklayıcıyı takın.

5. Kodunuzda kesme noktaları ayarlayın.

6. Kodlanmış UI test oluşturucusunda, mülk sağlayıcınızı çalıştıracak iddialılar oluşturun ve eylem filtrelerinizi uygulamak için eylemleri kaydedin.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.AccessibleObject>
- [Kodunuzu test etmek için UI otomasyonunu kullanma](../test/use-ui-automation-to-test-your-code.md)
