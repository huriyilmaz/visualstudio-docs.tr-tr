---
title: Benzersiz bir otomasyon özelliği ayarlama - UWP denetimlerini test etme
description: Kodlanmış ui testi çalıştırmak için XAML tabanlı UWP uygulamanıza XAML denetimi türüne göre benzersiz bir otomasyon özelliği atamayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 05/31/2018
ms.topic: how-to
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- uwp
author: mikejo5000
ms.openlocfilehash: b41e4e62d5691ffa6bd1caa4bfb87ac9ace16d9d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122068523"
---
# <a name="set-a-unique-automation-property-for-uwp-controls-for-testing"></a>Test için UWP denetimleri için benzersiz bir otomasyon özelliği ayarlama

XAML tabanlı UWP uygulamanız için kodlanmış UI testleri çalıştırmak için her denetimin benzersiz bir otomasyon özelliğiyle tanımlanmış olması gerekir. Uygulamanıza XAML denetimi türüne göre benzersiz bir otomasyon özelliği atabilirsiniz.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="static-xaml-definition"></a>Statik XAML tanımı

XAML dosyanız içinde tanımlanan bir denetim için benzersiz bir otomasyon özelliği belirtmek için, aşağıdaki örneklerde gösterildiği gibi **AutomationProperties.AutomationId** veya **AutomationProperties.Name'i** örtülü veya açık olarak ayarlayın. Bu değerlerden birini belirlemek, denetime, kodlanmış ui testi veya eylem kaydı oluşturma sırasında denetimi tanımlamak için kullanılan benzersiz bir otomasyon özelliği sağlar.

### <a name="set-the-property-implicitly"></a>Özelliği örtülü olarak ayarlama

Denetim için XAML'de Name özelliğini  kullanarak **AutomationProperties.AutomationId'i** **ButtonX** olarak ayarlayın.

```xaml
<Button Name="ButtonX" Height="31" HorizontalAlignment="Left" Margin="23,26,0,0"  VerticalAlignment="Top" Width="140" Click="ButtonX_Click" />
```

Denetimin **AutomationProperties.Name** **XAML'de** **Content** özelliğini kullanarak düğmeyi ButtonY olarak ayarlayın.

```xaml
<Button Content="ButtonY" Height="31" HorizontalAlignment="Left" Margin="23,76,0,0" VerticalAlignment="Top" Width="140" Click="ButtonY_Click" />
```

### <a name="set-the-property-explicitly"></a>Özelliği açıkça ayarlama

Denetim **için XAML'de AutomationProperties.AutomationId'i** **Açıkça ButtonX** olarak ayarlayın.

```xaml
<Button AutomationProperties.AutomationId="ButtonX" Height="31" HorizontalAlignment="Left" Margin="23,26,0,0"  VerticalAlignment="Top" Width="140" Click="ButtonX_Click" />
```

Denetim **için AutomationProperties.Name** **XAML'de** açıkça ButtonY olarak ayarlayın.

```xaml
<Button AutomationProperties.Name="ButtonY" Height="31" HorizontalAlignment="Left" Margin="23,76,0,0" VerticalAlignment="Top" Width="140" Click="ButtonY_Click" />
```

## <a name="assign-unique-names"></a>Benzersiz adlar atama

Bu Visual Studio için Blend düğmeler, liste kutuları, birleşik giriş kutuları ve metin kutuları gibi etkileşimli öğelere benzersiz adlar atama seçeneğini kullanabilirsiniz. Bu seçenek, denetimlere **AutomationProperties.Name.**

Mevcut denetimlere benzersiz adlar atamak için Araçlar Adı **Etkileşimli**  >  **Öğeler'i seçin.**

![Visual Studio için Blend'de Etkileşimli Öğeleri Visual Studio için Blend](../test/media/cuit_windowsstoreproperty_blend_1.png)

Otomatik olarak yeni denetimlere benzersiz adlar eklemek için Araçlar **Seçenekler'i**  >  **seçerek** Seçenekler iletişim **kutusunu** açın. Yeni **XAML Tasarımcısı'yi** seçin ve ardından **Etkileşimli öğeleri oluşturmada otomatik olarak adla'ya seçin.** İletişim **kutusunu** kapatmak için Tamam'ı seçin.

## <a name="use-a-data-template"></a>Veri şablonu kullanma

Liste kutusunda yer alan değerleri değişkenlere bağlamak **için ItemTemplate** kullanarak basit bir şablon tanımlayabilirsiniz:

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

Değerleri değişkenlere bağlamak için **ItemContainerStyle** ile bir şablon da kullanabilirsiniz:

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

Bu örneklerin her ikisi için de, aşağıdaki kod örneğini kullanarak gösterildiği gibi **ItemSource'ın** **ToString()** yöntemini geçersiz kılmanız gerekir. Bağlama kullanarak her **veriye bağlı AutomationProperties.Name** için benzersiz bir otomasyon özelliği ayarlayamazsanız, bu kod AutomationProperties.Name değerinin ve benzersiz olduğundan emin olur. Otomasyon sistemi için benzersiz bir **değer Properties.Name** bu durumda yeterlidir.

> [!NOTE]
> Bu yaklaşım kullanılarak, liste öğesinin iç içeriği bağlama aracılığıyla Employee sınıfındaki bir dizeye de ayarlandırabilirsiniz. Örnekte gösterildiği gibi, her liste öğesinin içindeki düğme denetimine çalışan kimliği olan benzersiz bir otomasyon kimliği atanır.

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

Belirli bir türün her örneği kodda tanımlandığı zaman benzersiz bir otomasyon özelliği elde etmek için bir denetim şablonu kullanabilirsiniz. **AutomationProperty'nin denetim örneğinde** benzersiz bir kimlik bağlaması için şablonu oluşturun. Aşağıdaki XAML, denetim şablonuyla bu bağlamayı oluşturmak için bir yaklaşımı gösteriyor:

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

Bu denetim şablonunu kullanarak düğmenin iki örneğini tanımladığınız zaman, otomasyon kimliği aşağıdaki XAML'de gösterildiği gibi şablonda denetimler için benzersiz içerik dizesine ayarlanır:

```xaml
<Button Content="Button1" Style="{StaticResource MyButton}" Width="140"/>
<Button Content="Button2" Style="{StaticResource MyButton}" Width="140"/>
```

### <a name="dynamic-controls"></a>Dinamik denetimler

Kodunuzdan dinamik olarak oluşturulan ve statik olarak veya XAML dosyalarındaki şablonlar aracılığıyla oluşturulmadan denetimler varsa, denetimin **İçerik** veya **Ad** özelliklerini ayarlamanız gerekir. Bu eylem, her dinamik denetimin benzersiz bir otomasyon özelliğine sahip olduğundan emin olur. Örneğin, bir liste öğesi seçerek görüntülenecek bir onay kutusunu varsa, bu özellikleri burada gösterildiği gibi ayarlayın:

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

- [Kodlanmış UI testleriyle UWP uygulamalarını test edin](../test/test-uwp-app-with-coded-ui-test.md)
