---
title: Xamarin.Forms ile uygulama oluşturmaya yönelik temel bilgileri öğrenin
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: d22b5186-9e03-4e85-afc9-7cbe28522a6d
caps.latest.revision: 14
ms.author: crdun
manager: crdun
ms.openlocfilehash: bc7e46af7e29ef554b80bd9244910e0c67d373af
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299764"
---
# <a name="learn-app-building-basics-with-xamarinforms-in-visual-studio"></a>Visual Studio'da Xamarin.Forms ile uygulama oluşturmaya yönelik temel bilgileri öğrenin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[Xamarin ortamınızı](../cross-platform/verify-your-xamarin-environment.md) [Kurulum ve](../cross-platform/setup-and-install.md) doğrulama adımlarını tamamladıktan sonra Bu izlenecek yol, Xamarin. Forms ile temel bir uygulamanın (aşağıda gösterilmiştir) nasıl oluşturulacağını gösterir. Xamarin.Forms ile UI kodunuzun tamamını kez taşınabilir sınıf kitaplığı (PCL) yazmanız. Xamarin sonra otomatik olarak işleme iOS, Android ve Windows için yerel kullanıcı Arabirimi denetimleri platformlar. Bu yaklaşım yalnızca bu .NET tüm hedef platformlar arasında desteklenen API'lerini kullanarak en iyi PCL seçeneğini desteklediği için önerilir ve Xamarin.Forms izin verdiğinden platformlar arasında UI kod paylaşın.

 ![Android, iOS ve Windows Phone Hava durumu uygulama örneği](../cross-platform/media/crossplat-xamarin-formsguide-1.png "Çapraz Splat Xamarin FormsGuide 1")

 Derlemek için bu işlemleri yapmanız:

- [Çözümünüzü ayarlama](#solution)

- [Paylaşılan veri hizmeti kodu yaz](#dataservice)

- [Paylaşılan UI kodu yazmaya başlayın](#uicode)

- [Android için Visual Studio öykünücüsü 'nü kullanarak uygulamanızı test etme](#test)

- [Platformları genelinde yerel bir görünüm ile Kullanıcı arabirimini tamamlama](#finish)

> [!TIP]
> Bu proje için tam kaynak kodunu [GitHub 'daki Xamarin-Forms-Samples deposunda](https://github.com/xamarin/xamarin-forms-samples/tree/master/Weather)bulabilirsiniz.

## <a name="solution"></a>Çözümünüzü ayarlama
 Bu adımlar paylaşılan kod için bir PCL ve iki eklenen NuGet paketlerini içeren bir Xamarin.Forms çözümü oluşturun.

1. Visual Studio 'da yeni bir **boş uygulama (Xamarin. Forms taşınabilir)** çözümü oluşturun ve bunu bir **hava uygulama**adıyla adlandırın. Bu şablonu, arama alanına **Xamarin. Forms** girerek en kolay şekilde bulabilirsiniz.

     Bu yoksa, Xamarin 'i yüklemek veya Visual Studio 2015 özelliğini etkinleştirmek zorunda kalabilirsiniz. [Kurulum ve yükleme](../cross-platform/setup-and-install.md)bölümüne bakın.

     ![Yeni bir boş uygulama &#40;oluşturma Xamarin. Forms taşınabilir&#41; projesi](../cross-platform/media/crossplat-xamarin-formsguide-2.png "Çapraz Splat Xamarin FormsGuide 2")

2. Çözümü oluşturmak için Tamam'a tıkladıktan sonra bir dizi ayrı projeler gerekir:

    - **Dalgalı uygulama (taşınabilir)** : Xamarin. Forms ile kullanılan ortak iş mantığı ve Kullanıcı arabirimi kodu dahil olmak üzere platformlar arasında paylaşılan kod yazacağınız PCL.

    - **Dalgalı uygulama. DROID**: Yerel Android kodunu içeren proje. Bu, varsayılan başlangıç projesi olarak ayarlanır.

    - **Dalgalı uygulama. iOS**: Yerel iOS kodunu içeren proje.

    - **Dalgalı uygulama. UWP**: WINDOWS 10 UWP kodu içeren proje.

    - **Dalgalı uygulama. Windows (Windows 8.1)** : yerel Windows 8.1 kodu içeren proje.

    - **Dalgalı uygulama. WinPhone (Windows Phone 8,1)** : yerel Windows Phone kodunu içeren proje.

    > [!NOTE]
    > Projelerin değil hedeflediğiniz platform için silmek boş. Bu izlenecek yolda amacı doğrultusunda, biz Android, iOS ve Windows Phone 8.1 projeleri başvuran. UWP ve Windows 8.1 ile çalışma projeleri Windows Phone 8.1 projesiyle çalışmaya çok benzer.

     Her yerel proje içinde karşılık gelen bir platform için yerel Tasarımcı erişimi vardır ve platform belirli ekranları ve gerektiğinde işlevi uygulayabilirsiniz.

3. Çözümünüzdeki Xamarin.Forms NuGet paketi gibi en son kararlı sürüme yükseltin. Yeni bir Xamarin çözümü oluşturduğunuzda bunu öneririz:

    - **NuGet paket yöneticisi > Araçlar ' ı seçin > çözüm Için NuGet paketlerini yönetin**.

    - **Güncelleştirmeler** sekmesi altında, **Xamarin. Forms** güncelleştirmesini denetleyin ve çözümünüzde tüm projeleri güncelleştirmek için denetleyin. (Not: tüm güncelleştirmeler için Xamarin.Android.Support işaretlemeden bırakın.)

    - **Sürüm** alanını kullanılabilir **en son kararlı** sürüme güncelleştirin.

    - **Güncelleştir**' e tıklayın.

         ![Xamarin. Forms NuGet paketini güncelleştirme](../cross-platform/media/crossplat-xamarin-formsguide-4.png "Çapraz Splat Xamarin FormsGuide 4")

4. **Newtonsoft. JSON** ve NuGet paketini bir hava durumu veri hizmetinden alınan bilgileri işlemek IÇIN kullanacağınız PCL projesine ekleyin:

    - NuGet Paket Yöneticisi 'nde (3. adımdan hala açık), **Gözden** geçirme sekmesini seçin ve **Newtonsoft**için arama yapın.

    - **Newtonsoft. JSON**öğesini seçin.

    - **Hava uygulama** projesini denetleyin (Bu, paketi yüklemeniz gereken tek projem ' dir).

    - **Sürüm** alanının **en son kararlı** sürüme ayarlandığından emin olun.

    - **Yükle**'ye tıklayın.

    - ![Newtonsoft. JSON NuGet paketini bulma ve yükleme](../cross-platform/media/crossplat-xamarin-formsguide-5.png "Çapraz Splat Xamarin FormsGuide 5")

5. **Microsoft.net. http** paketini bulmak ve yüklemek için 4. adımı yineleyin.

6. Çözümünüzü oluşturun ve herhangi bir yapı hatası olmadığını doğrulayın.

## <a name="dataservice"></a>Paylaşılan veri hizmeti kodu yaz
 **Hava uygulama (taşınabilir)** projesi, tüm platformlarda paylaşılan taşınabilir sınıf KITAPLıĞı (PCL) için kod yazacağınız yerdir. PCL otomatik olarak uygulamaya dahil edilen paketleri iOS, Android ve Windows Phone projeleri oluşturun.

 Bu örneği çalıştırmak için, ilk olarak [http://openweathermap.org/appid](https://openweathermap.org/appid)BIR ücretsiz API anahtarına kaydolmanız gerekir.

 Aşağıdaki adımlar bu durumda, hava durumu hizmetinden veri depolamak ve erişmek için PCL kodu ekleyin:

1. **Dalgalı uygulama** projesine sağ tıklayın ve **> Sınıf Ekle...** seçeneğini belirleyin. **Yeni öğe Ekle** iletişim kutusunda dosyayı **Weather.cs**olarak adlandırın. Bu sınıf, hava durumu verileri hizmetten alınan verileri depolamak için kullanacaksınız.

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

## <a name="uicode"></a>Paylaşılan UI kodu yazmaya başlayın
 Xamarin.Forms PCL'de paylaşılan kullanıcı Arabirimi kodunu uygulamak olanak tanır. Bu adımlarda PCL ile hizmet yazısının verilerle hava durumu verilerini tarafından döndürülen güncelleştirmeleri önceki bölümde eklediğiniz kodun bir düğme için bir ekran ekleyeceksiniz:

1. **WeatherPage.cs** adlı bir **Forms XAML sayfası** ekleyerek, **dalgalı uygulama** projesine sağ tıklayıp **> yeni öğe Ekle... öğesini**seçin. **Yeni öğe Ekle** iletişim kutusunda, "formlar," **form xaml seçin sayfasında**arama yapın ve **WeatherPage.cs**olarak adlandırın.

     Xamarin. Forms XAML tabanlıdır, bu nedenle bu adım iç içe geçmiş arka plan kod dosyası **WeatherPage.xaml.cs**dosya ile birlikte bir **hava sayfası. xaml** dosyası oluşturur. Bu, kullanıcı Arabirimi XAML veya kod aracılığıyla oluşturmanıza olanak sağlar. Bu kılavuzda hem de bazı yaparsınız.

     ![Yeni bir Xamarin. Forms XAML sayfası ekleme](../cross-platform/media/crossplat-xamarin-formsguide-6.png "Çapraz Splat Xamarin FormsGuide 6")

2. WeatherPage ekranına bir düğme eklemek için WeatherPage.xaml içeriğini aşağıdakiyle değiştirin:

    ```xaml
    <?xml version="1.0" encoding="utf-8" ?>
    <ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
           xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
           x:Class="WeatherApp.WeatherPage">
      <Button x:Name="getWeatherBtn" Text="Get Weather"/>
    </ContentPage>
    ```

     Düğme adının **x:Name** özniteliği kullanılarak tanımlanması gerektiğini ve bu düğmeye, arka plan kod dosyasının içinden ada göre başvurabilmeniz gerektiğini unutmayın.

3. Düğme metnini güncelleştirmek için düğmenin **tıklanmış** olayına bir olay işleyicisi eklemek için, **WeatherPage.xaml.cs** içeriğini aşağıdaki kodla değiştirin. ("60601" değiştirmek için başka bir posta kodu çekinmeyin.)

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

5. Kodu doğru olduğundan emin olmak için WeatherApp PCL projeyi derleyin.

## <a name="test"></a>Android için Visual Studio öykünücüsü 'nü kullanarak uygulamanızı test etme
 Uygulamayı çalıştırmak artık hazırsınız! Uygulama hava durumu hizmetinden veri alma doğrulamak şimdilik yalnızca Android sürümü çalıştıralım. Daha sonra daha fazla kullanıcı Arabirimi öğeleri ekledikten sonra da iOS ve Windows Phone sürümlerinde çalıştıracaksınız. (Not: Windows 7'de Visual Studio kullanıyorsanız, aynı adımları ancak bunun yerine Xamarin Player olur.)

1. Daha sonra sağ tıklayıp **Başlangıç projesi olarak ayarla**' yı seçerek, **dalgalı uygulama. DROID** projesini başlangıç projesi olarak ayarlayın.

2. Visual Studio araç çubuğunda, hedef proje olarak listelenmiş olan **dalgalı uygulama. DROID** ' yi görürsünüz. Hata ayıklama için Android öykünücülerinden birini seçin ve **F5**tuşuna basın. Android için Visual Studio öykünücüsü seçeneklerinde uygulamayı çalıştıracak **vs öykünücü** seçeneklerinden birini kullanmanızı öneririz.

     ![VS öykünücüsü hata ayıklama hedefi seçme](../cross-platform/media/crossplat-xamarin-formsguide-7.png "Çapraz Splat Xamarin FormsGuide 7")

3. Uygulama öykünücüsünde başlatıldığında **Hava durumu Al** düğmesine tıklayın. Düğme metnini, hava durumu hizmetinden alınan verilerin *title* özelliği olan **Chicago, Il**'ye güncelleştirildiğini görmeniz gerekir.

     ![Düğmeye dokunmadan önce ve sonra hava durumu uygulaması](../cross-platform/media/crossplat-xamarin-formsguide-8.png "Çapraz Splat Xamarin FormsGuide 8")

## <a name="finish"></a>Platformları genelinde yerel bir görünüm ile Kullanıcı arabirimini tamamlama
 Uygulamanızı otomatik olarak yerel bir görünümüne sahip olacak şekilde Xamarin.Forms her platform için yerel kullanıcı Arabirimi denetimleri oluşturur. Bunu görmek için daha net bir şekilde, bir posta kodu için giriş alanını kullanıcı Arabirimiyle şimdi son ve ardından hizmetten döndürülen hava durumu verilerini görüntüleyebilirsiniz.

1. **Dalgalı Therpage. xaml** içeriğini aşağıdaki kodla değiştirin. Her öğenin, daha önce açıklandığı gibi **X:Name** özniteliği kullanılarak adlandırıldığına ve öğenin koddan başvurulabilmesini sağlayabilirsiniz. Xamarin. Forms ayrıca çeşitli [Düzen seçenekleri](https://docs.microsoft.com/xamarin/xamarin-forms/user-interface/controls/layouts) (Xamarin.com) sağlar; burada, dalgalı sayfa [StackLayout](https://docs.microsoft.com/dotnet/api/Xamarin.Forms.StackLayout?view=xamarin-forms) (Xamarin.com) kullanıyor.

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

    Xamarin. Forms içinde **Onplatform** etiketinin kullanımını göz önünde edin. **Onplatform** , uygulamanın çalıştığı geçerli platforma özgü bir özellik değeri seçer (bkz. [dış XAML sözdizimi](https://docs.microsoft.com/xamarin/xamarin-forms/xaml/xaml-basics/essential-xaml-syntax) (Xamarin.com). Buraya bir veri alanları farklı metin rengini ayarlamak için kullanıyoruz: Android ve Windows Phone, iOS siyah beyaz. XAML 'de herhangi bir yere platforma özgü ayarlamalar yapmak için herhangi bir özellik ve herhangi bir veri türü için **Onplatform** kullanabilirsiniz. Arka plan kod dosyasında, [Device. OnPlatform API](https://docs.microsoft.com/xamarin/xamarin-forms/platform/device) 'sini aynı amaçla kullanabilirsiniz.

2. **WeatherPage.xaml.cs**' de **GetWeatherBtn_Clicked** olay işleyicisini aşağıdaki kodla değiştirin. Bu kod, girişi alanında bir posta kodu, posta kodu için verileri alır, sonuçta elde edilen hava durumu örneği için tam ekran bağlama bağlamı ayarlar ve ardından "Tekrar arama." düğme metnini ayarlar doğrular. Kullanıcı arabirimindeki her bir etiket Hava durumu sınıfının bir özelliğine bağladığına, bu nedenle ekranın bağlama bağlamını bir **Hava durumu** örneğine ayarladığınızda, bu etiketlerin otomatik olarak güncelleştirilmesini sağlayabilirsiniz.

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

3. Uygulamayı üç tüm platformlarda çalıştırın; Android, iOS ve Windows Phone — uygun projeye sağ, başlangıç projesi olarak Ayarla'i seçerek ve uygulamayı bir cihaz veya öykünücü veya benzetici başlatılıyor. Geçerli bir Amerika Birleşik Devletleri posta kodu (örneğin, 60601) girin ve aşağıda gösterildiği gibi bu bölge için hava durumu verileri görüntülemek için hava durumu Al düğmesine basın. Elbette, Visual Studio iOS projesi için ağınızdaki bir Mac OS X bilgisayara bağlı olması gerekir.

    ![Android, iOS ve Windows Phone Hava durumu uygulama örneği](../cross-platform/media/crossplat-xamarin-formsguide-1.png "Çapraz Splat Xamarin FormsGuide 1")

   Bu proje için tam kaynak kodu [GitHub 'daki Xamarin-Forms-Samples deposunda](https://github.com/xamarin/xamarin-forms-samples/tree/master/Weather)bulunur.
