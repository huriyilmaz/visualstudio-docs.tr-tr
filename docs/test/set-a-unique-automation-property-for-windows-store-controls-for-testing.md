---
title: Test Etme Amacıyla UWP Denetimleri için Benzersiz Otomasyon Özelliği Ayarlama
ms.date: 05/31/2018
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
author: mikejo5000
ms.openlocfilehash: 51e16dcaa48a08ae97bc80be1d33163c6f3af875
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590455"
---
# <a name="set-a-unique-automation-property-for-uwp-controls-for-testing"></a>Test için UWP denetimleri için benzersiz bir otomasyon özelliği ayarlama

XAML tabanlı UWP uygulamanız için kodlanmış Kullanıcı Arabirimi testlerini çalıştırmak istiyorsanız, her denetim benzersiz bir otomasyon özelliği tarafından tanımlanmalıdır. Uygulamanızdaki XAML denetiminin türüne göre benzersiz bir otomasyon özelliği atayabilirsiniz.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="static-xaml-definition"></a>Statik XAML tanımı

XAML dosyanızda tanımlanan bir denetim için benzersiz bir otomasyon özelliği belirtmek için **AutomationProperties.AutomationId'i** **veya** AutomationProperties.Name aşağıdaki örneklerde gösterildiği gibi örtülü veya açık olarak ayarlayabilirsiniz. Bu değerlerden birini ayarlamak, denetime kodlanmış bir ui testi veya eylem kaydı oluşturduğunuzda denetimi tanımlamak için kullanılabilecek benzersiz bir otomasyon özelliği sağlar.

### <a name="set-the-property-implicitly"></a>Özelliği örtülü olarak ayarlama

Control için XAML'deki **Ad** özelliğini kullanarak **AutomationProperties.AutomationId'i** **ButtonX'e** ayarlayın.

```xaml
<Button Name="ButtonX" Height="31" HorizontalAlignment="Left" Margin="23,26,0,0"  VerticalAlignment="Top" Width="140" Click="ButtonX_Click" />
```

Denetim için XAML'deki **İçerik** özelliğini kullanarak **AutomationProperties.Name** **ButtonY** olarak ayarlayın.

```xaml
<Button Content="ButtonY" Height="31" HorizontalAlignment="Left" Margin="23,76,0,0" VerticalAlignment="Top" Width="140" Click="ButtonY_Click" />
```

### <a name="set-the-property-explicitly"></a>Özelliği açıkça ayarlama

Control için XAML'de **AutomationProperties.AutomationId'i** **ButtonX'e** ayarlayın.

```xaml
<Button AutomationProperties.AutomationId="ButtonX" Height="31" HorizontalAlignment="Left" Margin="23,26,0,0"  VerticalAlignment="Top" Width="140" Click="ButtonX_Click" />
```

Denetim için XAML'de **AutomationProperties.Name** açıkça **ButtonY** olarak ayarlayın.

```xaml
<Button AutomationProperties.Name="ButtonY" Height="31" HorizontalAlignment="Left" Margin="23,76,0,0" VerticalAlignment="Top" Width="140" Click="ButtonY_Click" />
```

## <a name="assign-unique-names"></a>Benzersiz adlar atama

Visual Studio için Karışım'da, denetimlere **AutomationProperties.Name**için benzersiz değerler veren düğmeler, liste kutuları, açılan kutular ve metin kutuları gibi etkileşimli öğelere benzersiz adlar atama seçeneğini seçebilirsiniz.

Varolan denetimlere benzersiz adlar atamak için **Araçlar** > **Adı Etkileşimli Öğeler'i**seçin.

![Visual Studio için Blend Adı İnteraktif Elemanları](../test/media/cuit_windowsstoreproperty_blend_1.png)

Eklediğiniz yeni denetimlere otomatik olarak benzersiz adlar vermek için **Seçenekler** iletişim kutusunu açmak için **Araçlar** > **Seçenekleri'ni** seçin. **XAML Designer'ı** seçin ve ardından **oluşturmada etkileşimli öğeleri otomatik olarak adlandır'ı**seçin. İletişim kutusunu kapatmak için **Tamam'ı** seçin.

## <a name="use-a-data-template"></a>Veri şablonu kullanma

Liste kutusundaki değerleri değişkenlere bağlamak için **ItemTemplate'i** kullanarak basit bir şablon tanımlayabilirsiniz:

```xaml
<ListBox Name="listBox1" ItemsSource="{Binding Source={StaticResource employees}}">
   <ListBox.ItemTemplate>
      <DataTemplate>
         <StackPanel Orientation="Horizontal">
            <TextBlock Text="{Binding EmployeeName}" />
            <TextBlock Text="{Binding EmployeeID}" />
         </StackPanel>
      </DataTemplate>
   </ListBox.ItemTemplate>
</ListBox>
```

Değerleri değişkenlere bağlamak için **ItemContainerStyle** ile birlikte bir şablon da kullanabilirsiniz:

```xaml
<ListBox Name="listBox1" ItemsSource="{Binding Source={StaticResource employees}}">
   <ListBox.ItemContainerStyle>
      <Style TargetType="ListBoxItem">
         <Setter Property="Template">
            <Setter.Value>
               <ControlTemplate TargetType="ListBoxItem">
                  <Grid>
                     <Button Content="{Binding EmployeeName}" AutomationProperties.AutomationId="{Binding EmployeeID}"/>
                  </Grid>
               </ControlTemplate>
            </Setter.Value>
         </Setter>
      </Style>
   </ListBox.ItemContainerStyle>
</ListBox>
```

Bu örneklerin her ikisi için de, aşağıdaki kod örneğini kullanarak gösterildiği gibi, **ItemSource'un** **ToString()** yöntemini geçersiz kılmanız gerekir. Bu kod, bağlama yı kullanarak her veriye bağlı liste öğesi için benzersiz bir otomasyon özelliği ayarlayamadığından, **AutomationProperties.Name** değerinin ayarlandığından ve benzersiz olduğundan emin olur. Bu durumda Otomasyon **Properties.Name** için benzersiz bir değer ayarlamak yeterlidir.

> [!NOTE]
> Bu yaklaşımı kullanarak, liste öğesinin iç içeriği bağlama yoluyla Çalışan sınıfında bir dize olarak da ayarlanabilir. Örnekte gösterildiği gibi, her liste öğesinin içindeki düğme denetimine Çalışan Kimliği olan benzersiz bir otomasyon kimliği atanır.

```csharp
Employee[] employees = new Employee[]
{
   new Employee("john", "4384"),
   new Employee("margaret", "7556"),
   new Employee("richard", "8688"),
   new Employee("george", "1293")
};

listBox1.ItemsSource = employees;

public override string ToString()
{
    return EmployeeName + EmployeeID; // Unique Identification to be set as the AutomationProperties.Name
}
```

## <a name="use-a-control-template"></a>Denetim şablonu kullanma

Belirli bir türün her örneğinin kodda tanımlandığında benzersiz bir otomasyon özelliği elde edilebilsin diye bir denetim şablonu kullanabilirsiniz. Şablonu, **AutomationProperty'in** denetim örneğinde benzersiz bir tağa bağlanması nı sağlayacak şekilde oluşturun. Aşağıdaki XAML, bu bağlamayı bir denetim şablonuyla oluşturmak için bir yaklaşım gösterir:

```xaml
<Style x:Key="MyButton" TargetType="Button">
<Setter Property="Template">
   <Setter.Value>
<ControlTemplate TargetType="Button">
   <Grid>
      <CheckBox HorizontalAlignment="Left" AutomationProperties.AutomationId="{TemplateBinding Content}"></CheckBox>
      <Button Width="90" HorizontalAlignment="Right" Content="{TemplateBinding Content}" AutomationProperties.AutomationId="{TemplateBinding Content}"></Button>
   </Grid>
</ControlTemplate>
   </Setter.Value>
</Setter>
</Style>
```

Bu denetim şablonu kullanılarak bir düğmenin iki örneğini tanımladığınızda, otomasyon kimliği aşağıdaki XAML'de gösterildiği gibi şablondaki denetimler için benzersiz içerik dizesi olarak ayarlanır:

```xaml
<Button Content="Button1" Style="{StaticResource MyButton}" Width="140"/>
<Button Content="Button2" Style="{StaticResource MyButton}" Width="140"/>
```

### <a name="dynamic-controls"></a>Dinamik kontroller

Kodunuzdan dinamik olarak oluşturulan ve statik olarak veya XAML dosyalarındaki şablonlar aracılığıyla oluşturulmayan denetimleriniz varsa, denetim için **İçerik** veya **Ad** özelliklerini ayarlamanız gerekir. Bu eylem, her dinamik denetimin benzersiz bir otomasyon özelliğine sahip olmasını sağlar. Örneğin, bir liste öğesi seçtiğinizde görüntülenmesi gereken bir onay kutunuz varsa, burada gösterildiği gibi bu özellikleri ayarlayabilirsiniz:

```csharp
private void CreateCheckBox(string txt, StackPanel panel)
{
   CheckBox cb = new CheckBox();
   cb.Content = txt; // Sets the AutomationProperties.Name
   cb.Height = 50;
   cb.Width = 100;
   cb.Name = "DynamicCheckBoxAid"+ txt; // Sets the AutomationProperties.AutomationId
   panel.Children.Add(cb);
}
```

## <a name="see-also"></a>Ayrıca bkz.

- [UWP uygulamalarını kodlanmış UI testleriyle test edin](../test/test-uwp-app-with-coded-ui-test.md)
