---
title: Xamarin. Forms ile uygulama oluşturma temelleri hakkında bilgi edinin
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: d22b5186-9e03-4e85-afc9-7cbe28522a6d
caps.latest.revision: 14
ms.author: crdun
manager: crdun
ms.openlocfilehash: 09da3bd59163cbef8b33b1d5ece732330e32eac7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75918927"
---
# <a name="learn-app-building-basics-with-xamarinforms-in-visual-studio"></a>Visual Studio'da Xamarin.Forms ile uygulama oluşturmaya yönelik temel bilgileri öğrenin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[Xamarin ortamınızı](../cross-platform/verify-your-xamarin-environment.md) [Kurulum ve](../cross-platform/setup-and-install.md) doğrulama adımlarını tamamladıktan sonra Bu izlenecek yol, Xamarin. Forms ile temel bir uygulamanın (aşağıda gösterilmiştir) nasıl oluşturulacağını gösterir. Xamarin. Forms ile, bir taşınabilir sınıf kitaplığı 'nda (PCL) bir kez kullanıcı arabirimi kodunuzu yazabilirsiniz. Xamarin daha sonra iOS, Android ve Windows platformları için yerel UI denetimlerini otomatik olarak işler. Bu yaklaşım, yalnızca tüm hedef platformlarda desteklenen .NET API 'Lerini kullanmayı en iyi şekilde desteklediğinden ve Xamarin. Forms, platformlar arasında kullanıcı arabirimi kodu paylaşmanıza olanak sağladığından bu yaklaşımı öneririz.

 ![Android, iOS ve Windows Phone Hava durumu uygulama örneği](../cross-platform/media/crossplat-xamarin-formsguide-1.png "Çapraz Splat Xamarin FormsGuide 1")

 Bunu oluşturmak için şunları yapabilirsiniz:

- [Çözümünüzü ayarlama](#solution)

- [Paylaşılan veri hizmeti kodu yaz](#dataservice)

- [Paylaşılan UI kodu yazmaya başlayın](#uicode)

- [Android için Visual Studio öykünücüsü 'nü kullanarak uygulamanızı test etme](#test)

- [Platformları genelinde yerel bir görünüm ile Kullanıcı arabirimini tamamlama](#finish)

> [!TIP]
> Bu proje için tam kaynak kodunu [GitHub 'daki Xamarin-Forms-Samples deposunda](https://github.com/xamarin/xamarin-forms-samples/tree/master/Weather)bulabilirsiniz.

## <a name="set-up-your-solution"></a><a name="solution"></a> Çözümünüzü ayarlama
 Bu adımlar, paylaşılan kod için PCL ve iki adet eklenen NuGet paketi içeren bir Xamarin. Forms çözümü oluşturur.

1. Visual Studio 'da yeni bir **boş uygulama (Xamarin. Forms taşınabilir)** çözümü oluşturun ve bunu bir **hava uygulama**adıyla adlandırın. Bu şablonu, arama alanına **Xamarin. Forms** girerek en kolay şekilde bulabilirsiniz.

     Bu yoksa, Xamarin 'i yüklemek veya Visual Studio 2015 özelliğini etkinleştirmek zorunda kalabilirsiniz. [Kurulum ve yükleme](../cross-platform/setup-and-install.md)bölümüne bakın.

     ![Yeni boş bir App &#40;Xamarin. Forms taşınabilir&#41; projesi oluşturma](../cross-platform/media/crossplat-xamarin-formsguide-2.png "Çapraz Splat Xamarin FormsGuide 2")

2. Çözümü oluşturmak için Tamam ' a tıkladıktan sonra bir dizi bağımsız projeniz olacaktır:

    - **Dalgalı uygulama (taşınabilir)**: Xamarin. Forms ile kullanılan ortak iş mantığı ve Kullanıcı arabirimi kodu dahil olmak üzere platformlar arasında paylaşılan kod yazacağınız PCL.

    - **Dalgalı uygulama. DROID**: Yerel Android kodunu içeren proje. Bu, varsayılan başlangıç projesi olarak ayarlanır.

    - **Dalgalı uygulama. iOS**: Yerel iOS kodunu içeren proje.

    - **Dalgalı uygulama. UWP**: WINDOWS 10 UWP kodu içeren proje.

    - **Dalgalı uygulama. Windows (Windows 8.1)**: yerel Windows 8.1 kodu içeren proje.

    - **Dalgalı uygulama. WinPhone (Windows Phone 8,1)**: yerel Windows Phone kodunu içeren proje.

    > [!NOTE]
    > Hedeflenmiyor bir platforma ait herhangi bir projeyi silmek ücretsizdir. Bu izlenecek yolun amaçları doğrultusunda Android, iOS ve Windows Phone 8,1 projelerine başvuracağız. UWP ve Windows 8.1 projelerle çalışma, Windows Phone 8,1 projesiyle çalışmaya çok benzer.

     Her yerel projede, karşılık gelen platform için yerel tasarımcıya erişebilirsiniz ve gerektiğinde platforma özel ekranlar ve işlevler uygulayabilirsiniz.

3. Çözümünüzdeki Xamarin. Forms NuGet paketini aşağıdaki şekilde en son kararlı sürüme yükseltin. Bunu, her yeni bir Xamarin çözümü oluşturduğunuzda yapmanızı öneririz:

    - **NuGet paket yöneticisi > Araçlar ' ı seçin > çözüm Için NuGet paketlerini yönetin**.

    - **Güncelleştirmeler** sekmesi altında, **Xamarin. Forms** güncelleştirmesini denetleyin ve çözümünüzde tüm projeleri güncelleştirmek için denetleyin. (Note: Xamarin. Android için herhangi bir güncelleştirme yok. desteği işaretlenmemiş.)

    - **Sürüm** alanını kullanılabilir **en son kararlı** sürüme güncelleştirin.

    - **Güncelleştir**’e tıklayın.

         ![Xamarin. Forms NuGet paketini güncelleştirme](../cross-platform/media/crossplat-xamarin-formsguide-4.png "Çapraz Splat Xamarin FormsGuide 4")

4. **Newtonsoft.Js** ve NuGet paketini bir hava durumu veri hizmetinden alınan bilgileri işlemek IÇIN kullanacağınız PCL projesine ekleyin:

    - NuGet Paket Yöneticisi 'nde (3. adımdan hala açık), **Gözden** geçirme sekmesini seçin ve **Newtonsoft**için arama yapın.

    - **Newtonsoft.Js**seçin.

    - **Hava uygulama** projesini denetleyin (Bu, paketi yüklemeniz gereken tek projem ' dir).

    - **Sürüm** alanının **en son kararlı** sürüme ayarlandığından emin olun.

    - **Yükle**'ye tıklayın.

    - ![NuGet paketine Newtonsoft.Jsbulma ve yükleme](../cross-platform/media/crossplat-xamarin-formsguide-5.png "Çapraz Splat Xamarin FormsGuide 5")

5. **Microsoft.net. http** paketini bulmak ve yüklemek için 4. adımı yineleyin.

6. Çözümünüzü derleyin ve derleme hatası olmadığını doğrulayın.

## <a name="write-shared-data-service-code"></a><a name="dataservice"></a> Paylaşılan veri hizmeti kodu yaz
 **Hava uygulama (taşınabilir)** projesi, tüm platformlarda paylaşılan taşınabilir sınıf KITAPLıĞı (PCL) için kod yazacağınız yerdir. PCL, iOS, Android ve Windows Phone projeleri tarafından oluşturulacak uygulama paketlerine otomatik olarak eklenir.

 Bu örneği çalıştırmak için, ilk olarak bir ücretsiz API anahtarına kaydolmanız gerekir [http://openweathermap.org/appid](https://openweathermap.org/appid) .

 Aşağıdaki adımlar, bu hava durumu hizmetine erişmek ve verileri depolamak için PCL 'e kod ekler:

1. **Dalgalı uygulama** projesine sağ tıklayın ve **> Sınıf Ekle...** seçeneğini belirleyin. **Yeni öğe Ekle** iletişim kutusunda dosyayı **Weather.cs**olarak adlandırın. Bu sınıfı, hava durumu verileri hizmetinden veri depolamak için kullanacaksınız.

2. **Weather.cs** öğesinin tüm içeriğini aşağıdaki kodla değiştirin:

    ```csharp
    namespace WeatherApp
    {
        public class Weather
        {
            public string Title { get; set; }
            public string Temperature { get; set; }
            public string Wind { get; set; }
            public string Humidity { get; set; }
            public string Visibility { get; set; }
            public string Sunrise { get; set; }
            public string Sunset { get; set; }

            public Weather()
            {
                //Because labels bind to these values, set them to an empty string to
                //ensure that the label appears on all platforms by default.
                this.Title = " ";
                this.Temperature = " ";
                this.Wind = " ";
                this.Humidity = " ";
                this.Visibility = " ";
                this.Sunrise = " ";
                this.Sunset = " ";
            }
        }
    }
    ```

3. **DataService.cs** adlı PCL projesine, hava durumu VERI hizmetindeki JSON verilerini işlemek için kullanacağınız başka bir sınıf ekleyin.

4. **DataService.cs** öğesinin tüm içeriğini aşağıdaki kodla değiştirin:

    ```csharp
    using System.Threading.Tasks;
    using Newtonsoft.Json;
    using System.Net.Http;

    namespace WeatherApp
    {
        public class DataService
        {
            public static async Task<dynamic> getDataFromService(string queryString)
            {
                HttpClient client = new HttpClient();
                var response = await client.GetAsync(queryString);

                dynamic data = null;
                if (response != null)
                {
                    string json = response.Content.ReadAsStringAsync().Result;
                    data = JsonConvert.DeserializeObject(json);
                }

                return data;
            }
        }
    }
    ```

5. Bir veri kümesi kodu ile bir sorgu dizesi oluşturan, hava durumu verileri hizmetini çağıran ve **Hava durumu** sınıfının bir örneğini dolduran Logic gibi paylaşılan iş mantığını YERLEŞTIRECEĞINIZ, PCL adlı **çekirdeğe** üçüncü bir sınıf ekleyin.

6. **Core.cs** içeriğini aşağıdaki kodla değiştirin:

    ```csharp
    using System;
    using System.Threading.Tasks;

    namespace WeatherApp
    {
        public class Core
        {
            public static async Task<Weather> GetWeather(string zipCode)
            {
                //Sign up for a free API key at http://openweathermap.org/appid
                string key = "YOUR KEY HERE";
                string queryString = "http://api.openweathermap.org/data/2.5/weather?zip="
                    + zipCode + ",us&appid=" + key + "&units=imperial";

                dynamic results = await DataService.getDataFromService(queryString).ConfigureAwait(false);

                if (results["weather"] != null)
                {
                    Weather weather = new Weather();
                    weather.Title = (string)results["name"];
                    weather.Temperature = (string)results["main"]["temp"] + " F";
                    weather.Wind = (string)results["wind"]["speed"] + " mph";
                    weather.Humidity = (string)results["main"]["humidity"] + " %";
                    weather.Visibility = (string)results["weather"][0]["main"];

                    DateTime time = new System.DateTime(1970, 1, 1, 0, 0, 0, 0);
                    DateTime sunrise = time.AddSeconds((double)results["sys"]["sunrise"]);
                    DateTime sunset = time.AddSeconds((double)results["sys"]["sunset"]);
                    weather.Sunrise = sunrise.ToString() + " UTC";
                    weather.Sunset = sunset.ToString() + " UTC";
                    return weather;
                }
                else
                {
                    return null;
                }
            }
        }
    }
    ```

7. Kodun doğru olduğundan emin olmak için **dalgalı uygulama** PCL projesi oluşturun.

## <a name="begin-writing-shared-ui-code"></a><a name="uicode"></a> Paylaşılan UI kodu yazmaya başlayın
 Xamarin. Forms, PCL 'de paylaşılan UI kodu uygulamanıza olanak sağlar. Bu adımlarda, bir önceki bölümde eklenen Hava durumu veri hizmeti kodu tarafından döndürülen verilerle birlikte metin güncelleştiren bir düğme ile PCL 'e bir ekran ekleyeceksiniz:

1. **WeatherPage.cs** adlı bir **Forms XAML sayfası** ekleyerek, **dalgalı uygulama** projesine sağ tıklayıp **> yeni öğe Ekle... öğesini**seçin. **Yeni öğe Ekle** iletişim kutusunda, "formlar," **form xaml seçin sayfasında**arama yapın ve **WeatherPage.cs**olarak adlandırın.

     Xamarin. Forms XAML tabanlıdır, bu nedenle bu adım iç içe geçmiş arka plan kod dosyası **WeatherPage.xaml.cs**dosya ile birlikte bir **hava sayfası. xaml** dosyası oluşturur. Bu, XAML veya kod aracılığıyla UI oluşturmanıza olanak sağlar. Bu kılavuzda her ikisini de gerçekleştirirsiniz.

     ![Yeni bir Xamarin. Forms XAML sayfası ekleme](../cross-platform/media/crossplat-xamarin-formsguide-6.png "Çapraz Splat Xamarin FormsGuide 6")

2. Dalgalı sayfa ekranına bir düğme eklemek için, dalgalı Therpage. XAML içeriğini aşağıdakiler ile değiştirin:

    ```xaml
    <?xml version="1.0" encoding="utf-8" ?>
    <ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
           xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
           x:Class="WeatherApp.WeatherPage">
      <Button x:Name="getWeatherBtn" Text="Get Weather"/>
    </ContentPage>
    ```

     Düğme adının **x:Name** özniteliği kullanılarak tanımlanması gerektiğini ve bu düğmeye, arka plan kod dosyasının içinden ada göre başvurabilmeniz gerektiğini unutmayın.

3. Düğme metnini güncelleştirmek için düğmenin **tıklanmış** olayına bir olay işleyicisi eklemek için, **WeatherPage.xaml.cs** içeriğini aşağıdaki kodla değiştirin. ("60601" öğesini başka bir ZIP koduna değiştirebilirsiniz.)

    ```csharp
    using System;
    using Xamarin.Forms;

    namespace WeatherApp
    {
        public partial class WeatherPage: ContentPage
        {
            public WeatherPage()
            {
                InitializeComponent();
                this.Title = "Sample Weather App";
                getWeatherBtn.Clicked += GetWeatherBtn_Clicked;

                //Set the default binding to a default object for now
                this.BindingContext = new Weather();
            }

            private async void GetWeatherBtn_Clicked(object sender, EventArgs e)
            {
                Weather weather = await Core.GetWeather("60601");
                getWeatherBtn.Text = weather.Title;
            }
        }
    }
    ```

4. Uygulama başlatıldığında **dalgalı sayfa** 'yı ilk ekran olarak açmak için **app.cs** içindeki varsayılan oluşturucuyu şu kodla değiştirin:

    ```csharp
    public App()
    {
        MainPage = new NavigationPage(new WeatherPage());
    }
    ```

5. Kodun doğru olduğundan emin olmak için dalgalı uygulama PCL projesi oluşturun.

## <a name="test-your-app-using-the-visual-studio-emulator-for-android"></a><a name="test"></a> Android için Visual Studio öykünücüsü 'nü kullanarak uygulamanızı test etme
 Şimdi uygulamayı çalıştırmaya hazırsınız! Şimdi uygulamanın Hava durumu hizmetinden veri aldığını doğrulamak için yalnızca Android sürümünü çalıştıralım. Daha sonra, daha fazla kullanıcı arabirimi öğesi ekledikten sonra iOS ve Windows Phone sürümlerini de çalıştırabilirsiniz. (Note: Windows 7 ' de Visual Studio çalıştırıyorsanız, bu adımları takip edersiniz, ancak bunun yerine Xamarin oynatıcı olacaktır.)

1. Daha sonra sağ tıklayıp **Başlangıç projesi olarak ayarla**' yı seçerek, **dalgalı uygulama. DROID** projesini başlangıç projesi olarak ayarlayın.

2. Visual Studio araç çubuğunda, hedef proje olarak listelenmiş olan **dalgalı uygulama. DROID** ' yi görürsünüz. Hata ayıklama için Android öykünücülerinden birini seçin ve **F5**tuşuna basın. Android için Visual Studio öykünücüsü seçeneklerinde uygulamayı çalıştıracak **vs öykünücü** seçeneklerinden birini kullanmanızı öneririz.

     ![VS öykünücüsü hata ayıklama hedefi seçme](../cross-platform/media/crossplat-xamarin-formsguide-7.png "Çapraz Splat Xamarin FormsGuide 7")

3. Uygulama öykünücüsünde başlatıldığında **Hava durumu Al** düğmesine tıklayın. Düğme metnini, hava durumu hizmetinden alınan verilerin *title* özelliği olan **Chicago, Il**'ye güncelleştirildiğini görmeniz gerekir.

     ![Düğmeye dokunmadan önce ve sonra hava durumu uygulaması](../cross-platform/media/crossplat-xamarin-formsguide-8.png "Çapraz Splat Xamarin FormsGuide 8")

## <a name="finish-the-ui-with-a-native-look-and-feel-across-platforms"></a><a name="finish"></a> Platformları genelinde yerel bir görünüm ile Kullanıcı arabirimini tamamlama
 Xamarin. Forms, uygulamanızın otomatik olarak yerel bir görünüm olmasını sağlamak için her platform için yerel kullanıcı arabirimi denetimlerini işler. Bunu daha net bir şekilde görmek için, Kullanıcı arabirimini bir ZIP kodu için bir giriş alanı ile tamamlayalım ve sonra hizmetten döndürülen Hava durumu verilerini görüntüleriz.

1. **Dalgalı Therpage. xaml** içeriğini aşağıdaki kodla değiştirin. Her öğenin, daha önce açıklandığı gibi **X:Name** özniteliği kullanılarak adlandırıldığına ve öğenin koddan başvurulabilmesini sağlayabilirsiniz. Xamarin. Forms ayrıca çeşitli [Düzen seçenekleri](/xamarin/xamarin-forms/user-interface/controls/layouts) (Xamarin.com) sağlar; burada, dalgalı sayfa [StackLayout](/dotnet/api/Xamarin.Forms.StackLayout?view=xamarin-forms) (Xamarin.com) kullanıyor.

   ```xaml
   <?xml version="1.0" encoding="utf-8" ?>
   <ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
          xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
          x:Class="WeatherApp.WeatherPage">

     <ContentPage.Resources>
       <ResourceDictionary>
         <Style x:Key="labelStyle" TargetType="Label">
           <Setter Property="TextColor" Value="#a8a8a8" />
           <Setter Property="FontSize" Value="Small" />
         </Style>
         <Style x:Key="fieldStyle" TargetType="Label">
           <Setter Property="TextColor">
             <OnPlatform x:TypeArguments="Color" iOS="Black" Android="White" WinPhone="White" />
           </Setter>
           <Setter Property="FontSize" Value="Medium" />
         </Style>
         <Style x:Key="fieldView" TargetType="ContentView">
           <Setter Property="Padding" Value="10,0,0,0" />
         </Style>
       </ResourceDictionary>
     </ContentPage.Resources>

     <ContentPage.Content>
       <ScrollView>
         <StackLayout>
           <StackLayout Orientation="Horizontal" HorizontalOptions="FillAndExpand"
                 BackgroundColor="#545454">
             <StackLayout Padding="10,10,10,10" HorizontalOptions="Start">
               <Label Text="Search by Zip Code" TextColor="White" FontAttributes="Bold"
                   FontSize="Medium" />
               <Label x:Name="zipCodeLabel" Text="Zip Code" Style="{StaticResource labelStyle}" />
               <Entry x:Name="zipCodeEntry" />
             </StackLayout>
             <StackLayout Padding="0,0,0,10" VerticalOptions="End">
               <Button x:Name="getWeatherBtn" Text="Get Weather" WidthRequest="185" BorderWidth="1" >
                 <!-- Set iOS colors; use defaults on other platforms -->
                 <Button.TextColor>
                   <OnPlatform x:TypeArguments="Color" iOS="White"/>
                 </Button.TextColor>
                 <Button.BorderColor>
                   <OnPlatform x:TypeArguments="Color" iOS="White"/>
                 </Button.BorderColor>
               </Button>
             </StackLayout>
           </StackLayout>
           <StackLayout Padding="10,10,10,10" HorizontalOptions="Start">
             <Label Text="Location" Style="{StaticResource labelStyle}" />
             <ContentView Style="{StaticResource fieldView}">
               <Label Text="{Binding Title}" Style="{StaticResource fieldStyle}" />
             </ContentView>
             <Label Text="Temperature" Style="{StaticResource labelStyle}" />
             <ContentView Style="{StaticResource fieldView}">
               <Label x:Name="tempLabel" Text="{Binding Temperature}"
                   Style="{StaticResource fieldStyle}" />
             </ContentView>
             <Label Text="Wind Speed" Style="{StaticResource labelStyle}" />
             <ContentView Style="{StaticResource fieldView}">
               <Label x:Name="windLabel" Text="{Binding Wind}" Style="{StaticResource fieldStyle}" />
             </ContentView>
             <Label Text="Humidity" Style="{StaticResource labelStyle}" />
             <ContentView Style="{StaticResource fieldView}">
               <Label x:Name="humidityLabel" Text="{Binding Humidity}"
                   Style="{StaticResource fieldStyle}" />
             </ContentView>
             <Label Text="Visibility" Style="{StaticResource labelStyle}" />
             <ContentView Style="{StaticResource fieldView}">
               <Label x:Name="visibilitylabel" Text="{Binding Visibility}"
                   Style="{StaticResource fieldStyle}" />
             </ContentView>
             <Label Text="Time of Sunrise" Style="{StaticResource labelStyle}" />
             <ContentView Style="{StaticResource fieldView}">
               <Label x:Name="sunriseLabel" Text="{Binding Sunrise}"
                   Style="{StaticResource fieldStyle}" />
             </ContentView>
             <Label Text="Time of Sunset" Style="{StaticResource labelStyle}" />
             <ContentView Style="{StaticResource fieldView}">
               <Label x:Name="sunsetLabel" Text="{Binding Sunset}"
                   Style="{StaticResource fieldStyle}" />
             </ContentView>
           </StackLayout>
         </StackLayout>
       </ScrollView>
     </ContentPage.Content>
   </ContentPage>
   ```

    Xamarin. Forms içinde **Onplatform** etiketinin kullanımını göz önünde edin. **Onplatform** , uygulamanın çalıştığı geçerli platforma özgü bir özellik değeri seçer (bkz. [dış XAML sözdizimi](/xamarin/xamarin-forms/xaml/xaml-basics/essential-xaml-syntax) (Xamarin.com). Veri alanları için farklı bir metin rengi ayarlamak üzere burada kullanıyoruz: Android ve Windows Phone üzerinde beyaz, iOS üzerinde siyah. XAML 'de herhangi bir yere platforma özgü ayarlamalar yapmak için herhangi bir özellik ve herhangi bir veri türü için **Onplatform** kullanabilirsiniz. Arka plan kod dosyasında, [Device. OnPlatform API](/xamarin/xamarin-forms/platform/device) 'sini aynı amaçla kullanabilirsiniz.

2. **WeatherPage.xaml.cs**' de **GetWeatherBtn_Clicked** olay işleyicisini aşağıdaki kodla değiştirin. Bu kod, giriş alanında bir posta kodu bulunduğunu doğrular, bu posta kodu için verileri alır, ekranın tüm bağlama bağlamını ortaya çıkan hava durumu örneğine ayarlar ve sonra düğme metnini "yeniden ara" olarak ayarlar. Kullanıcı arabirimindeki her bir etiket Hava durumu sınıfının bir özelliğine bağladığına, bu nedenle ekranın bağlama bağlamını bir **Hava durumu** örneğine ayarladığınızda, bu etiketlerin otomatik olarak güncelleştirilmesini sağlayabilirsiniz.

   ```csharp
   private async void GetWeatherBtn_Clicked(object sender, EventArgs e)
   {
       if (!String.IsNullOrEmpty(zipCodeEntry.Text))
       {
           Weather weather = await Core.GetWeather(zipCodeEntry.Text);
           this.BindingContext = weather;
           getWeatherBtn.Text = "Search Again";
       }
   }
   ```

3. İlgili projeye sağ tıklayıp başlangıç projesi olarak ayarla ' yı seçerek ve uygulamayı bir cihazda ya da öykünücü veya benzeticide başlatarak, her üç platformda (Android, iOS ve Windows Phone) uygulamayı çalıştırın. Geçerli bir Birleşik Devletler ZIP kodu girin (örneğin, 60601) ve aşağıda gösterildiği gibi bu bölgeye ait hava durumu verilerini göstermek için hava durumu Al düğmesine basın. İOS projesi için ağınızdaki bir Mac OS X bilgisayara Visual Studio 'nun bağlı olması gerekir.

    ![Android, iOS ve Windows Phone Hava durumu uygulama örneği](../cross-platform/media/crossplat-xamarin-formsguide-1.png "Çapraz Splat Xamarin FormsGuide 1")

   Bu proje için tam kaynak kodu [GitHub 'daki Xamarin-Forms-Samples deposunda](https://github.com/xamarin/xamarin-forms-samples/tree/master/Weather)bulunur.
