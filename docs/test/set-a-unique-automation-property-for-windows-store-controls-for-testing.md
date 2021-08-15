---
title: Benzersiz bir Otomasyon özelliği ayarlama-test UWP denetimleri
description: Kodlanmış UI testi çalıştırmak için XAML tabanlı UWP uygulamanızda XAML denetiminin türüne göre benzersiz bir Otomasyon özelliği atamayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 05/31/2018
ms.topic: how-to
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- uwp
author: mikejo5000
ms.openlocfilehash: 73ccfe2ec8562e27f284082c8cd0f577427b01c937ad32b77e0c6cea16787f47
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121315102"
---
# <a name="set-a-unique-automation-property-for-uwp-controls-for-testing"></a>Test için UWP denetimleri için benzersiz bir Otomasyon özelliği ayarlama

XAML tabanlı UWP uygulamanız için kodlanmış UI testlerini çalıştırmak istiyorsanız, her denetim benzersiz bir Otomasyon özelliği ile tanımlanmalıdır. Uygulamanızdaki XAML denetiminin türüne göre benzersiz bir Otomasyon özelliği atayabilirsiniz.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="static-xaml-definition"></a>Statik XAML tanımı

XAML dosyanızda tanımlanan bir denetim için benzersiz bir Otomasyon özelliği belirtmek için, aşağıdaki örneklerde gösterildiği gibi **AutomationProperties. AutomationId** veya **AutomationProperties.Name** öğesini örtük veya açık olarak ayarlayabilirsiniz. Bu değerlerden birini ayarlamak, kodlanmış UI testi veya eylem kaydı oluştururken denetimi tanımlamak için kullanılabilen benzersiz bir Otomasyon özelliği sağlar.

### <a name="set-the-property-implicitly"></a>Özelliği örtük olarak ayarlayın

Denetimin XAML içindeki **Name** özelliğini kullanarak **AutomationProperties. AutomationId** öğesini **buttonx** olarak ayarlayın.

```xaml
<Button Name="ButtonX" Height="31" HorizontalAlignment="Left" Margin="23,26,0,0"  VerticalAlignment="Top" Width="140" Click="ButtonX_Click" />
```

Denetimin XAML içindeki **Content** özelliğini kullanarak **AutomationProperties.Name** öğesini **buttony** olarak ayarlayın.

```xaml
<Button Content="ButtonY" Height="31" HorizontalAlignment="Left" Margin="23,76,0,0" VerticalAlignment="Top" Width="140" Click="ButtonY_Click" />
```

### <a name="set-the-property-explicitly"></a>Özelliği açıkça ayarla

Denetim için XAML 'de **AutomationProperties. AutomationId** öğesini **buttonx** olarak ayarlayın.

```xaml
<Button AutomationProperties.AutomationId="ButtonX" Height="31" HorizontalAlignment="Left" Margin="23,26,0,0"  VerticalAlignment="Top" Width="140" Click="ButtonX_Click" />
```

Denetimin XAML içinde **AutomationProperties.Name** öğesini **buttony** olarak ayarlayın.

```xaml
<Button AutomationProperties.Name="ButtonY" Height="31" HorizontalAlignment="Left" Margin="23,76,0,0" VerticalAlignment="Top" Width="140" Click="ButtonY_Click" />
```

## <a name="assign-unique-names"></a>Benzersiz adlar ata

Visual Studio için Blend ' de, denetimler, liste kutuları, birleşik giriş kutuları ve metin kutuları gibi etkileşimli öğelere benzersiz adlar atamak için bir seçenek belirleyebilirsiniz. bu, denetimleri **AutomationProperties.Name** için benzersiz değerler sağlar.

Varolan denetimlere benzersiz adlar atamak için **Araçlar**  >  **adı etkileşimli öğeler**' i seçin.

![Visual Studio için Blend etkileşimli öğeleri adlandırın](../test/media/cuit_windowsstoreproperty_blend_1.png)

Eklediğiniz yeni denetimlere otomatik olarak benzersiz adlar vermek için,   >  **Seçenekler** iletişim kutusunu açmak üzere Araçlar **Seçenekler** ' i seçin. **XAML Tasarımcısı** ' yi seçin ve sonra **otomatik olarak etkileşimli öğeleri oluşturma '** yı seçin. İletişim kutusunu kapatmak için **Tamam ' ı** seçin.

## <a name="use-a-data-template"></a>Veri şablonu kullanma

Bir liste kutusundaki değerleri değişkenlere bağlamak için **ItemTemplate** kullanarak basit bir şablon tanımlayabilirsiniz:

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

Ayrıca, değerlerini değişkenlere bağlamak için **ItemContainerStyle** içeren bir şablon da kullanabilirsiniz:

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

Bu örneklerin her ikisi için de, aşağıdaki kod örneğini kullanarak gösterildiği gibi **ItemSource** için **ToString ()** yöntemini geçersiz kılmanız gerekir. Bu kod, bağlama kullanarak her bir veri bağlama listesi öğesi için benzersiz bir Otomasyon özelliği ayarlayamadığı için **AutomationProperties.Name** değerinin ayarlanmış ve benzersiz olduğundan emin olur. Bu durumda **Automation Properties.Name** için benzersiz bir değer ayarlanması yeterlidir.

> [!NOTE]
> Bu yaklaşımı kullanarak, liste öğesinin iç içeriği, bağlama yoluyla çalışan sınıfında bir dizeye de ayarlanabilir. Örnekte gösterildiği gibi, her liste öğesinin içindeki düğme denetimine, çalışan KIMLIĞI olan benzersiz bir Otomasyon kimliği atanır.

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

Belirli bir türün her örneğinin, kodda tanımlandığında benzersiz bir Otomasyon özelliği elde edebilmesi için bir denetim şablonu kullanabilirsiniz. **AutomationProperty** öğesinin denetim örneğindeki BENZERSIZ bir kimliğe bağlaması için şablonu oluşturun. Aşağıdaki XAML, bu bağlamayı bir denetim şablonuyla oluşturmak için bir yaklaşımı gösterir:

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

Bu denetim şablonunu kullanarak bir düğmenin iki örneğini tanımladığınızda, aşağıdaki XAML 'de gösterildiği gibi, Otomasyon KIMLIĞI şablondaki denetimlerin benzersiz içerik dizesine ayarlanır:

```xaml
<Button Content="Button1" Style="{StaticResource MyButton}" Width="140"/>
<Button Content="Button2" Style="{StaticResource MyButton}" Width="140"/>
```

### <a name="dynamic-controls"></a>Dinamik denetimler

Kodunuzda dinamik olarak veya XAML dosyalarındaki şablonlar aracılığıyla oluşturulan denetimleriniz varsa, denetimin **içerik** veya **ad** özelliklerini ayarlamanız gerekir. Bu eylem, her dinamik denetimin benzersiz bir Otomasyon özelliğine sahip olduğundan emin olur. Örneğin, bir liste öğesini seçtiğinizde gösterilmesi gereken bir onay kutusu varsa, bu özellikleri burada gösterildiği gibi ayarlayabilirsiniz:

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

- [Kodlanmış UI Testleriyle UWP uygulamalarını test etme](../test/test-uwp-app-with-coded-ui-test.md)
