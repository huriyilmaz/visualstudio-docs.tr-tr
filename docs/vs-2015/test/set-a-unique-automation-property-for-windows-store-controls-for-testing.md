---
title: Test için Windows Mağazası denetimleri için benzersiz bir Otomasyon özelliği ayarla | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 9bdd74ff-2534-4fc7-a5c3-a77bf7843037
caps.latest.revision: 12
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d4ccf10f3ce085aa8f0275c40644f1a109616daf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672144"
---
# <a name="set-a-unique-automation-property-for-windows-store-controls-for-testing"></a>Test yapma amacıyla Windows Mağazası Denetimleri için Benzersiz Otomasyon Özelliği ayarlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

XAML tabanlı Windows Mağazası uygulamanız için kodlanmış UI testlerini çalıştırmak istiyorsanız, her bir denetimi tanımlayan benzersiz bir Otomasyon özelliğine sahip olmanız gerekir.

 Uygulamanızdaki XAML denetiminin türüne göre benzersiz bir Otomasyon özelliği atayabilirsiniz. Aşağıdaki durumlarda bu benzersiz Otomasyon özelliğinin nasıl atanacağı aşağıda verilmiştir:

- [Denetimlerin statik XAML tanımı](#UniquePropertyWindowsStoreControlsStaticXAML)

- [Visual Studio veya Visual Studio için Blend kullanarak benzersiz Otomasyon özellikleri atama](#UniquePropertyWindowsStoreControlsExpressionBlend)

- [DataTemplate kullanma](#UniquePropertyWindowsStoreControlsDataTemplate)

- [Denetim şablonu kullanma](#UniquePropertyWindowsStoreControlsControlTemplate)

- [Dinamik denetimler](#UniquePropertyWindowsStoreControlsDynamicControls)

## <a name="use-methods-to-assign-a-unique-automation-property"></a>Benzersiz bir Otomasyon özelliği atamak için yöntemleri kullanma

### <a name="static-xaml-definition"></a><a name="UniquePropertyWindowsStoreControlsStaticXAML"></a> Statik XAML tanımı
 XAML dosyanızda tanımlanan bir denetim için benzersiz bir Otomasyon özelliği belirtmek için, aşağıdaki örneklerde gösterildiği gibi AutomationProperties. AutomationId veya AutomationProperties.Name öğesini örtük veya açık olarak ayarlayabilirsiniz. Bu değerlerden birini ayarlamak, kodlanmış UI testi veya eylem kaydı oluştururken denetimi tanımlamak için kullanılabilen benzersiz bir Otomasyon özelliği sağlar.

 **Özelliği örtük olarak ayarlayın**

 Denetimin XAML içindeki Name özelliğini kullanarak AutomationProperties. AutomationId öğesini **Buttonx** olarak ayarlayın.

```xaml
<Button Name="ButtonX" Height="31" HorizontalAlignment="Left" Margin="23,26,0,0"  VerticalAlignment="Top" Width="140" Click="ButtonX_Click" />

```

 Denetimin XAML içindeki Content özelliğini kullanarak AutomationProperties.Name öğesini **buttony** olarak ayarlayın.

```xaml
<Button Content="ButtonY" Height="31" HorizontalAlignment="Left" Margin="23,76,0,0" VerticalAlignment="Top" Width="140" Click="ButtonY_Click" />

```

 **Özelliği açıkça ayarla**

 AutomationProperties. AutomationId öğesini denetimin XAML içinde açıkça **Buttonx** olarak ayarlayın.

```xaml
<Button AutomationProperties.AutomationId=“ButtonX” Height="31" HorizontalAlignment="Left" Margin="23,26,0,0"  VerticalAlignment="Top" Width="140" Click="ButtonX_Click" />

```

 Denetimin XAML içinde AutomationProperties.Name öğesini **buttony** olarak ayarlayın.

```
<Button AutomationProperties.Name="ButtonY" Height="31" HorizontalAlignment="Left" Margin="23,76,0,0" VerticalAlignment="Top" Width="140" Click="ButtonY_Click" />
```

### <a name="assign-unique-automation-properties-using-visual-studio-or-blend-for-visual-studio"></a><a name="UniquePropertyWindowsStoreControlsExpressionBlend"></a> Visual Studio veya Visual Studio için Blend kullanarak benzersiz Otomasyon özellikleri atama
 Düğmeler, liste kutuları, Birleşik giriş kutuları ve metin kutuları gibi etkileşimli öğelere benzersiz adlar atamak için Visual Studio veya Visual Studio için Blend kullanabilirsiniz. Bu, denetimin AutomationProperties.Name için benzersiz bir değer sağlar.

 **Visual Studio:** **Araçlar** menüsünde **Seçenekler** ' in üzerine gelin ve ardından **metin Düzenleyicisi**, sonra **xaml**ve son ' u seçin **Miscellaneous**.

 **Oluşturma sırasında etkileşimli öğeleri otomatik olarak Adlandır** ' ı seçin ve **Tamam**' ı seçin.

 ![XAML çeşitli seçenekleri](../test/media/cuit-windowsstoreapp-b.png "CUIT_WindowsStoreApp_B")

 **Visual Studio için Blend:** Bunu Visual Studio için Blend yapmak için aşağıdaki yöntemlerden birini kullanın.

> [!NOTE]
> Bu yöntemi yalnızca XAML kullanılarak statik olarak oluşturulan denetimler için kullanabilirsiniz.

 **Varolan denetimlere benzersiz bir ad vermek için**

 **Araçlar** menüsünde, burada gösterildiği gibi **etkileşimli öğeleri Adlandır**' ı seçin:

 ![Araçlar menüsünden etkileşimli öğeleri Adlandır ' ı seçin](../test/media/cuit-windowsstoreproperty-blend-1.png "CUIT_WindowsStoreProperty_Blend_1")

 **Otomatik olarak oluşturduğunuz denetimlere benzersiz bir ad vermek için**

 **Araçlar** menüsünde **Seçenekler**' in üzerine gelin ve ardından **Proje**' yi seçin. **Oluşturma sırasında etkileşimli öğeleri otomatik olarak Adlandır** ' ı seçin ve ardından aşağıda gösterildiği gibi **Tamam**' ı seçin:

 ![Projeyi, etkileşimli öğeleri adlandırmak üzere ayarla](../test/media/cuit-windowsstoreproeprty-blend-2.png "CUIT_WindowsStoreProeprty_Blend_2")

### <a name="use-a-data-template"></a><a name="UniquePropertyWindowsStoreControlsDataTemplate"></a> Veri şablonu kullanma
 Aşağıdaki XAML 'yi kullanarak bir liste kutusundaki değerleri değişkenlere bağlamak için ItemTemplate kullanarak basit bir şablon tanımlayabilirsiniz.

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

 Ayrıca, aşağıdaki XAML kullanarak değerleri değişkenlere bağlamak için ItemContainerStyle içeren bir şablon da kullanabilirsiniz.

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

 Bu örneklerin her ikisi için de aşağıdaki kodu kullanarak gösterildiği gibi ItemSource öğesinin ToString () yöntemini geçersiz kılmanız gerekir. Bu kod, bağlamayı kullanarak her bir veri bağlama listesi öğesi için benzersiz bir Otomasyon özelliği ayarlayamadığı için AutomationProperties.Name değerinin ayarlanmış ve benzersiz olduğundan emin olur. Bu durumda Automation Properties.Name için benzersiz bir değer ayarlanması yeterlidir.

> [!NOTE]
> Bu yaklaşımı kullanarak, liste öğesinin iç içeriği, bağlama yoluyla çalışan sınıfında bir dizeye de ayarlanabilir. Örnekte gösterildiği gibi, her liste öğesinin içindeki düğme denetimine, çalışan KIMLIĞI olan benzersiz bir Otomasyon kimliği atanır.

```

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

### <a name="use-a-control-template"></a><a name="UniquePropertyWindowsStoreControlsControlTemplate"></a> Denetim şablonu kullanma
 Belirli bir türün her örneğinin, kodda tanımlandığında benzersiz bir Otomasyon özelliği elde edebilmesi için bir denetim şablonu kullanabilirsiniz. AutomationProperty öğesinin denetim örneğindeki benzersiz bir KIMLIĞE bağlaması için şablonu oluşturmanız gerekir. Aşağıdaki XAML, bu bağlamayı bir denetim şablonuyla oluşturmak için bir yaklaşımı gösterir.

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

 Bu denetim şablonunu kullanarak bir düğmenin iki örneğini tanımladığınızda, Otomasyon kimliği, aşağıdaki XAML 'de gösterildiği gibi şablondaki denetimler için benzersiz içerik dizesine ayarlanır.

```xaml

<Button Content=”Button1” Style="{StaticResource MyButton}" Width="140"/>
<Button Content=”Button2” Style="{StaticResource MyButton}" Width="140"/>
```

### <a name="dynamic-controls"></a><a name="UniquePropertyWindowsStoreControlsDynamicControls"></a> Dinamik denetimler
 Kodunuzda dinamik olarak veya XAML dosyalarındaki şablonlar aracılığıyla oluşturulan denetimleriniz varsa, denetimin Içerik veya ad özelliklerini ayarlamanız gerekir. Bu, her dinamik denetimin benzersiz bir Otomasyon özelliğine sahip olduğundan emin olmanızı sağlar. Örneğin, bir liste öğesini seçtiğinizde gösterilmesi gereken bir onay kutusu varsa, bu özellikleri burada gösterildiği gibi ayarlayabilirsiniz:

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
