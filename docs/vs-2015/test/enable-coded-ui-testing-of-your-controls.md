---
title: Denetimlerinizin kodlanmış UI testini etkinleştirin | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 5ef1188f-89dc-413d-801d-0efdaf9b0427
caps.latest.revision: 24
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7190a7f698868642c58d1de2ff801e328859b9db
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851803"
---
# <a name="enable-coded-ui-testing-of-your-controls"></a>Denetimlerinizin Kodlanmış UI Testlerini Etkinleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kodlanmış UI test çerçevesi için destek uygularsanız, denetiminiz daha kolay bir şekilde test edilebilir. Artan destek düzeylerini artımlı olarak ekleyebilirsiniz. Kayıt ve kayıttan yürütme ve özellik doğrulamasını destekleyerek başlayabilirsiniz. Bu özelliği, kodlanmış UI test oluşturucusunun denetiminizin özel özelliklerini tanımasını sağlamak ve oluşturulan koddan Bu özelliklere erişmek için özel sınıflar sağlamak üzere oluşturabilirsiniz. Ayrıca, kodlanmış UI Test Oluşturucusu yakalama eylemlerine, kaydedilen eylemin amacına daha yakın bir şekilde de yardımcı olabilirsiniz.

 **Bu konuda:**

1. [Erişilebilirliği uygulayarak kaydı ve kayıttan yürütmeyi ve özellik doğrulamasını destekleme](../test/enable-coded-ui-testing-of-your-controls.md#recordandplayback)

2. [Özellik sağlayıcısı uygulayarak özel özellik doğrulamasını destekleme](../test/enable-coded-ui-testing-of-your-controls.md#customproprties)

3. [Özel özelliklere erişmek için bir sınıf uygulayarak kod oluşturmayı destekleme](../test/enable-coded-ui-testing-of-your-controls.md#codegeneration)

4. [Bir eylem filtresi uygulayarak amaç kullanan eylemleri destekleme](../test/enable-coded-ui-testing-of-your-controls.md#intentawareactions)

   ![CUIT&#95;tam](../test/media/cuit-full.png "CUIT_Full")

## <a name="recordandplayback"></a>Erişilebilirliği uygulayarak kaydı ve kayıttan yürütmeyi ve özellik doğrulamasını destekleme
 Kodlanmış UI Test Oluşturucusu bir kayıt sırasında karşılaştığı denetimlerle ilgili bilgileri yakalar ve ardından bu oturumu yeniden oynatmak için kod üretir. Denetiminiz erişilebilirliği desteklemiyorsa, kodlanmış UI Test Oluşturucusu, ekran koordinatlarını kullanarak eylemleri (fare tıklamaları gibi) yakalar. Test kayıttan yürütüldüğünde, oluşturulan kod fare tıklamalarını aynı ekran koordinatlarına göre sağlar. Test kayıttan yürütüldüğünde denetiminiz ekran üzerinde farklı bir yerde görünüyorsa, oluşturulan kod denetimi bu eylemi gerçekleştiremez. Bu, test farklı ekran yapılandırmalarında, farklı ortamlarda veya Kullanıcı arabirimi düzeninde değişiklik yaptıktan sonra kayıttan yürütüldüğünde hatalara neden olabilir.

 ![CUıT&#95;recordnosupport](../test/media/cuit-recordnosupport.png "CUIT_RecordNoSupport")

 Ancak erişilebilirliği uygularsanız, kodlanmış UI Test Oluşturucusu bir testi kaydederken ve kod oluşturduğunda denetiminize ilişkin bilgileri yakalamak için bunu kullanır. Daha sonra, testi çalıştırdığınızda, Kullanıcı arabiriminde başka bir yerde olsa bile, oluşturulan kod bu olayları denetiinize karşı yeniden oynayacaktır. Test yazarları, denetiminizin temel özelliklerini kullanarak onaylar de oluşturabilir.

 ![CUIT&#95;kaydı](../test/media/cuit-record.png "CUIT_Record")

### <a name="to-support-record-and-playback-property-validation-and-navigation-for-a-windows-forms-control"></a>Windows Forms denetimi için kayıt ve kayıttan yürütmeyi, özellik doğrulamayı ve gezintiyi desteklemek için
 Aşağıdaki yordamda gösterildiği gibi denetiminiz için erişilebilirlik uygulayın ve <xref:System.Windows.Forms.AccessibleObject>ayrıntılı olarak açıklanmıştır.

 ![Erişilebilir CUıT&#95;](../test/media/cuit-accessible.png "CUIT_Accessible")

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

3. Alt denetim için başka bir erişilebilirlik nesnesi uygulayın ve bu erişilebilirlik nesnesini döndürecek şekilde alt denetimin <xref:System.Windows.Forms.Control.AccessibilityObject%2A> özelliğini geçersiz kılın.

4. Alt denetimin erişilebilirlik nesnesi için <xref:System.Windows.Forms.AccessibleObject.Bounds%2A>, <xref:System.Windows.Forms.AccessibleObject.Name%2A>, <xref:System.Windows.Forms.AccessibleObject.Parent%2A>, <xref:System.Windows.Forms.AccessibleObject.Role%2A>, <xref:System.Windows.Forms.AccessibleObject.State%2A>, <xref:System.Windows.Forms.AccessibleObject.Navigate%2A>ve <xref:System.Windows.Forms.AccessibleObject.Select%2A> özelliklerini ve yöntemlerini geçersiz kılın.

> [!NOTE]
> Bu konu, bu yordamdaki <xref:System.Windows.Forms.AccessibleObject> erişilebilirlik örneğiyle birlikte başlar ve sonra geri kalan yordamlarda bunun üzerinde oluşturulur. Erişilebilirlik örneğinin çalışan bir sürümünü oluşturmak istiyorsanız, bir konsol uygulaması oluşturun ve Program.cs içindeki kodu örnek kodla değiştirin. Erişilebilirlik, System. Drawing ve System. Windows. Forms 'a başvuru eklemeniz gerekir. Bir yapı uyarısını ortadan kaldırmak için erişilebilirlik için **birlikte ekleme türlerini** **false** olarak değiştirmeniz gerekir. Uygulamayı çalıştırdığınızda bir konsol penceresi görünmemesi için, projenin çıkış türünü **konsol** uygulamasından **Windows uygulaması** olarak değiştirebilirsiniz.

## <a name="customproprties"></a>Özellik sağlayıcısı uygulayarak özel özellik doğrulamasını destekleme
 Kayıt ve kayıttan yürütme ve Özellik doğrulama için temel destek uygulandıktan sonra, bir <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> eklentisi uygulayarak denetimin özel özelliklerini kodlanmış UI testleri için kullanılabilir hale getirebilirsiniz. Örneğin, aşağıdaki yordam, kodlanmış UI testlerinin grafik denetiminin CurveLegend alt denetimlerinin State özelliğine erişmesini sağlayan bir özellik sağlayıcısı oluşturur.

 ![CUIT&#95;customprops](../test/media/cuit-customprops.png "CUIT_CustomProps")

### <a name="to-support-custom-property-validation"></a>Özel özellik doğrulamasını desteklemek için
 ![CUıT&#95;props](../test/media/cuit-props.png "CUIT_Props")

1. Açıklama dizesinde zengin özellik değerlerini, ana açıklamadan (ve birden çok özellik uyguladığınızda birbirleriyle) noktalı virgülle (;) ayırarak) geçirerek, eğri göstergesi erişilebilir nesnenin <xref:System.Windows.Forms.AccessibleObject.Description%2A> özelliğini geçersiz kılın.

    ```csharp
    public class CurveLegendAccessibleObject : AccessibleObject
    {
        // add the state property value to the description
        public override string Description
        {
            get
            {
                // Add “;” and the state value to the end
                // of the curve legend’s description
                return "CurveLegend; " + State.ToString();
            }
        }
    }
    ```

2. Bir sınıf kitaplığı projesi oluşturup erişilebilirlik, Microsoft. VisualStudio. TestTools. Uıitedıya, Microsoft. VisualStudio. TestTools. UITest. Common ve Microsoft. VisualStudio. TestTools. Extension. Erişilebilirlik için **Embed Interop türlerini** **false**olarak değiştirin.

3. <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>türetilmiş bir özellik sağlayıcısı sınıfı ekleyin.

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

4. Özellik adlarını ve özellik tanımlayıcılarını bir <xref:System.Collections.Generic.Dictionary%602>yerleştirerek Özellik sağlayıcısını uygulayın.

    ```csharp
    // Define a map of property descriptors for CurveLegend
    private static Dictionary<string, UITestPropertyDescriptor> curveLegendPropertiesMap = null;
    private static Dictionary<string, UITestPropertyDescriptor> CurveLegendPropertiesMap
    {
        get
        {
            if (curveLegendPropertiesMap == null)
            {
                UITestPropertyAttributes read =
                    UITestPropertyAttributes.Readable |
                    UITestPropertyAttributes.DoNotGenerateProperties;
                curveLegendPropertiesMap =
                    new Dictionary<string, UITestPropertyDescriptor>
                        (StringComparer.OrdinalIgnoreCase);
                curveLegendPropertiesMap.Add("State",
                    new UITestPropertyDescriptor(typeof(string), read));
            }
            return curveLegendPropertiesMap;
        }
    }

    // return the property descriptor
    public override UITestPropertyDescriptor GetPropertyDescriptor(UITestControl uiTestControl, string propertyName)
    {
        return CurveLegendPropertiesMap[propertyName];
    }

    // return the property names
    public override ICollection<string> GetPropertyNames(UITestControl uiTestControl)
    {
        if (uiTestControl.ControlType.NameEquals("Chart") || uiTestControl.ControlType.NameEquals("Text"))
        {
            // the keys of the property map are the collection of property names
            return CurveLegendPropertiesMap.Keys;
        }

        // this is not my control
        throw new NotSupportedException();
    }

    // Get the property value by parsing the accessible description
    public override object GetPropertyValue(UITestControl uiTestControl, string propertyName)
    {
        if (String.Equals(propertyName, "State", StringComparison.OrdinalIgnoreCase))
        {
            object[] native = uiTestControl.NativeElement as object[];
            IAccessible acc = native[0] as IAccessible;

            string[] descriptionTokens = acc.accDescription.Split(new char[] { ';' });
            return descriptionTokens[1];
        }

        // this is not my control
        throw new NotSupportedException();
    }
    ```

5. Derlemenizi, denetiminiz ve alt öğeleri için denetime özgü destek sağladığını göstermek için <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetControlSupportLevel%2A?displayProperty=fullName> geçersiz kılın.

    ```csharp
    public override int GetControlSupportLevel(UITestControl uiTestControl)
    {
        // For MSAA, check the control type
        if (string.Equals(uiTestControl.TechnologyName, "MSAA",
            StringComparison.OrdinalIgnoreCase) &&
            (uiTestControl.ControlType == "Chart"||uiTestControl.ControlType == "Text"))
        {
            return (int)ControlSupport.ControlSpecificSupport;
        }

        // This is not my control, so return NoSupport
        return (int)ControlSupport.NoSupport;
    }
    ```

6. <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider?displayProperty=fullName>kalan soyut yöntemlerini geçersiz kılın.

    ```csharp
    public override string[] GetPredefinedSearchProperties(Type specializedClass)
    {
        throw new NotImplementedException();
    }

    public override Type GetSpecializedClass(UITestControl uiTestControl)
    {
        throw new NotImplementedException();
    }

    public override Type GetPropertyNamesClassType(UITestControl uiTestControl)
    {
        throw new NotImplementedException();
    }

    public override void SetPropertyValue(UITestControl uiTestControl, string propertyName, object value)
    {
        throw new NotImplementedException();
    }

    public override string GetPropertyForAction(UITestControl uiTestControl, UITestAction action)
    {
        throw new NotImplementedException();
    }

    public override string[] GetPropertyForControlState(UITestControl uiTestControl, ControlStates uiState, out bool[] stateValues)
    {
        throw new NotImplementedException();
    }

    ```

7. <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>türetilmiş bir uzantı paketi sınıfı ekleyin.

    ```csharp
    using System;
    using Microsoft.VisualStudio.TestTools.UITesting;
    using Microsoft.VisualStudio.TestTools.UITest.Extension;
    using Microsoft.VisualStudio.TestTools.UITest.Common;

    namespace ChartControlExtensionPackage
    {
        internal class ChartControlExtensionPackage : UITestExtensionPackage
        {
        }
    }
    ```

8. Derleme için `UITestExtensionPackage` özniteliğini tanımlayın.

    ```csharp
    [assembly: Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage(
                    "ChartControlExtensionPackage",
                    typeof(ChartControlExtensionPackage.ChartControlExtensionPackage))]
    namespace ChartControlExtensionPackage
    {
       …
    ```

9. Uzantı paketi sınıfında, bir özellik sağlayıcısı istendiğinde, özellik sağlayıcısı sınıfını döndürmek için <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A?displayProperty=fullName> geçersiz kılın.

    ```csharp
    internal class ChartControlExtensionPackage : UITestExtensionPackage
    {
        public override object GetService(Type serviceType)
        {
            if (serviceType == typeof(UITestPropertyProvider))
            {
                if (propertyProvider == null)
                {
                    propertyProvider = new ChartControlPropertyProvider();
                }
                return propertyProvider;
            }
            return null;
        }

        private UITestPropertyProvider propertyProvider = null;
    }
    ```

10. <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>kalan soyut yöntemleri ve özellikleri geçersiz kılın.

    ```csharp

    public override void Dispose() { }

    public override string PackageDescription
    {
        get { return "Supports coded UI testing of ChartControl"; }
    }

    public override string PackageName
    {
        get { return "ChartControl Test Extension"; }
    }

    public override string PackageVendor
    {
        get { return "Microsoft (sample)"; }
    }

    public override Version PackageVersion
    {
        get { return new Version(1, 0); }
    }

    public override Version VSVersion
    {
        get { return new Version(10, 0); }
    }
    ```

11. İkili dosyalarınızı derleyin ve **%ProgramFiles%\common\microsoft Shared\VSTT\10.0\UITestExtensionPackages**öğesine kopyalayın.

> [!NOTE]
> Bu uzantı paketi "metin" türünde herhangi bir denetime uygulanacak. Aynı türde birden çok denetimi test ediyorsanız, bunları ayrı olarak test etmeniz ve Testleri kaydettiğinizde hangi uzantı paketlerinin dağıtılacağını yönetmeniz gerekir.

## <a name="codegeneration"></a>Özel özelliklere erişmek için bir sınıf uygulayarak kod oluşturmayı destekleme
 Kodlanmış UI Test Oluşturucusu bir oturum kaydından kod oluşturduğunda, denetimleriniz erişmek için <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl> sınıfını kullanır.

```csharp

      UITestControl uIAText = this.UIItemWindow.UIChartControlWindow.UIAText;
Assert.AreEqual(this.AssertMethod3ExpectedValues.UIATextState, uIAText.GetProperty("State").ToString());
```

 Denetiminizin özel özelliklerine erişim sağlamak için bir özellik sağlayıcısı uyguladıysanız, oluşturulan kodun basitleşilmesi için bu özelliklere erişmek üzere kullanılan özel bir sınıf ekleyebilirsiniz.

```csharp

      ControlLegend uIAText = this.UIItemWindow.UIChartControlWindow.UIAText;
Assert.AreEqual(this.AssertMethod3ExpectedValues.UIATextState, uIAText.State);
```

### <a name="to-add-a-specialized-class-to-access-your-control"></a>Denetime erişmek için özel bir sınıf eklemek için
 ![CUıT&#95;CodeGen](../test/media/cuit-codegen.png "CUIT_CodeGen")

1. <xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls.WinControl> türetilen bir sınıf uygulayın ve denetimin türünü oluşturucuda arama özellikleri koleksiyonuna ekleyin.

    ```csharp
    public class CurveLegend:WinControl
    {
       public CurveLegend(UITestControl c) : base(c)
       {
          // The curve legend control is a “text” type of control
          SearchProperties.Add(
             UITestControl.PropertyNames.ControlType, "Text");
       }
    }
    ```

2. Denetimin özel özelliklerini sınıfının özellikleri olarak uygulayın.

    ```csharp
    public virtual string State
    {
        get
        {
            return (string)GetProperty("State");
        }
    }
    ```

3. Eğri gösterge alt denetimleri için yeni sınıfın türünü döndürmek üzere özellik sağlayıcınızın <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetSpecializedClass%2A?displayProperty=fullName> yöntemini geçersiz kılın.

    ```csharp
    public override Type GetSpecializedClass(UITestControl uiTestControl)
    {
       if (uiTestControl.ControlType.NameEquals("Text"))
       {
          // This is text type of control. For my control,
          // that means it’s a curve legend control.
          return typeof(CurveLegend);
       }

       // this is not a curve legend control
       return null;
    }
    ```

4. Yeni sınıf ' PropertyNames yönteminin türünü döndürmek için özellik sağlayıcınızın <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetPropertyNamesClassType%2A> yöntemini geçersiz kılın.

    ```csharp
    public override Type GetPropertyNamesClassType(UITestControl uiTestControl)
    {
        if (uiTestControl.ControlType.NameEquals("Text"))
        {
          // This is text type of control. For my control,
          // that means it’s a curve legend control.
            return typeof(CurveLegend.PropertyNames);
        }

        // this is not a curve legend control
        return null;
    }
    ```

## <a name="intentawareactions"></a>Bir eylem filtresi uygulayarak amaç kullanan eylemleri destekleme
 Visual Studio bir testi kaydeder, her fare ve klavye olayını yakalar. Ancak bazı durumlarda, eylemin amacı fare ve klavye olayları dizisinde kaybolabilir. Örneğin, denetiminiz otomatik tamamlamayı destekliyorsa, test farklı bir ortamda kayıttan yürütüldüğünde aynı fare ve klavye olayları kümesi farklı bir değer oluşmasına neden olabilir. Klavye ve fare olaylarının serisini tek bir eylemle değiştiren bir eylem filtresi eklentisi ekleyebilirsiniz. Bu şekilde, bir değer seçiminde değeri ayarlayan tek bir eylemle sonuçlanan fare ve klavye olaylarının serisini değiştirebilirsiniz. Bunun yapılması, kodlanmış UI testlerini bir ortamdan diğerine AutoComplete 'teki farklılıklardan korur.

### <a name="to-support-intent-aware-actions"></a>Amaç kullanan eylemleri desteklemek için
 ![CUıT&#95;eylemleri](../test/media/cuit-actions.png "CUIT_Actions")

1. [Uitestactionfilter](/previous-versions/visualstudio/visual-studio-2012/dd985757(v=vs.110))öğesinden türetilmiş bir eylem filtresi sınıfı uygulayıp [ApplyTimeout](/previous-versions/visualstudio/visual-studio-2012/dd984649%28v%3dvs.110%29), [Kategori](/previous-versions/visualstudio/visual-studio-2012/dd986905(v=vs.110)), [etkin](/previous-versions/visualstudio/visual-studio-2012/dd985633(v=vs.110)), [FilterType](/previous-versions/visualstudio/visual-studio-2012/dd778726(v=vs.110)), [Grup](/previous-versions/visualstudio/visual-studio-2012/dd779219(v=vs.110)) ve [ad](/previous-versions/visualstudio/visual-studio-2012/dd998334(v=vs.110))özelliklerini geçersiz kılar.

    ```csharp
    internal class MyActionFilter : UITestActionFilter
    {
       // If the user actions we are aggregating exceeds the time allowed,
       // this filter is not applied. (The timeout is configured when the
       // test is run.)
       public override bool ApplyTimeout
       {
          get { return true; }
       }

       // Gets the category of this filter. Categories of filters
       // are applied in priority order.
       public override UITestActionFilterCategory Category
       {
          get { return UITestActionFilterCategory.PostSimpleToCompoundActionConversion; }
       }

       public override bool Enabled
       {
          get { return true; }
       }

       public override UITestActionFilterType FilterType
       {
          // This action filter operates on a single action
          get { return UITestActionFilterType.Unary; }
       }

       // Gets the name of the group to which this filter belongs.
       // A group can be enabled/disabled using configuration file.
       public override string Group
       {
          get { return "ChartControlActionFilters"; }
       }

       // Gets the name of this filter.
       public override string Name
       {
          get { return "Convert Double-Click to Single-Click"; }
       }
    ```

2. `UITestActionFilter.ProcessRule`geçersiz kıl. Buradaki örnek, tek bir tıklama eylemiyle birlikte çift tıklama eylemini değiştirir.

    ```csharp
    public override bool ProcessRule(IUITestActionStack actionStack)
    {
        if (actionStack.Count > 0)
        {
            MouseAction lastAction = actionStack.Peek() as MouseAction;
            if (lastAction != null)
            {
                if (lastAction.UIElement.ControlTypeName.Equals(
                     ControlType.Text.ToString(),
                     StringComparison.OrdinalIgnoreCase))
                {
                    if(lastAction.ActionType == MouseActionType.DoubleClick)
                    {
                        // Convert to single click
                        lastAction.ActionType = MouseActionType.Click;
                    }
                }
            }
        }
        // Do not stop aggregation
        return false;
    }
    ```

3. Eylem filtresini uzantı paketinizin <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A> yöntemine ekleyin.

    ```csharp
    public override object GetService(Type serviceType)
    {
       if (serviceType == typeof(UITestPropertyProvider))
       {
          if (propertyProvider == null)
          {
             propertyProvider = new PropertyProvider();
          }
          return propertyProvider;
       }
       else if (serviceType == typeof(UITestActionFilter))
       {
          if (actionFilter == null)
          {
             actionFilter = new RadGridViewActionFilter();
          }
          return actionFilter;
       }
       return null;
    }
    ```

4. İkili dosyalarınızı derleyin ve%ProgramFiles%\Common Files\Microsoft Shared\vstt\10.0\uitestextensionpackages' e kopyalayın.

> [!NOTE]
> Eylem filtresi, erişilebilirlik uygulamasına veya özellik sağlayıcısına bağlı değildir.

## <a name="debug-your-property-provider-or-action-filter"></a>Özellik sağlayıcınızda veya eylem süzgecinde hata ayıklayın
 Özellik sağlayıcınız ve eylem filtreniz, uygulamanızdan ayrı bir işlemde kodlanmış UI Test Oluşturucusu tarafından yüklenen ve çalıştırılan bir uzantı paketinde uygulanır.

#### <a name="to-debug-your-property-provider-or-action-filter"></a>Özellik sağlayıcınızdaki veya eylem filtreinizdeki hataları ayıklamak için

1. Uzantı paketinizin hata ayıklama sürümünü oluşturun. dll ve. pdb dosyalarını%ProgramFiles%\Common Files\Microsoft Shared\vstt\10.0\uitestextensionpackages' e kopyalayın.

2. Uygulamanızı çalıştırın (hata ayıklayıcıda değil).

3. Kodlanmış UI test oluşturucuyu çalıştırın.

     `codedUITestBuilder.exe  /standalone`

4. Hata ayıklayıcıyı codedUITestBuilder işlemine iliştirin.

5. Kodunuzda kesme noktaları ayarlayın.

6. Kodlanmış UI Test Oluşturucusu ' nda, özellik sağlayıcınızı alıştırmaya yönelik onaylar oluşturun ve eylem filtrelerinizi uygulamak için eylemleri kaydedin.

## <a name="external-resources"></a>Dış kaynaklar

### <a name="guidance"></a>Kılavuz
 [Visual Studio 2012 ile sürekli teslim için test etme – Bölüm 2: birim testi: Içini test etme](https://msdn.microsoft.com/library/jj159340.aspx)

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.AccessibleObject>
- [Kodunuzu Test Etmek için UI Otomasyonunu Kullanma](../test/use-ui-automation-to-test-your-code.md)
