---
title: Xamarin kullanarak yerel kullanıcı arabirimi ile uygulama oluşturma
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: tgt-pltfrm-cross-plat
ms.topic: conceptual
ms.assetid: 30f137e6-595d-4ce7-b8f5-415b07c1caa2
caps.latest.revision: 33
ms.author: crdun
manager: crdun
ms.openlocfilehash: 204d3ee68aace07ed19e5913309a122d6d775a0e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75918338"
---
# <a name="build-apps-with-native-ui-using-xamarin-in-visual-studio"></a>Visual Studio’da Xamarin kullanarak yerel kullanıcı arabirimi ile uygulama oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[Xamarin ortamınızı](../cross-platform/verify-your-xamarin-environment.md) [Kurulum ve](../cross-platform/setup-and-install.md) doğrulama adımlarını tamamladıktan sonra Bu izlenecek yol, yerel kullanıcı arabirimi katmanları ile temel bir Xamarin uygulamasının (aşağıda gösterilmiştir) nasıl oluşturulacağını gösterir. Yerel Kullanıcı arabirimi ile, paylaşılan kod taşınabilir bir sınıf kitaplığında (PCL) bulunur ve tek platform projeleri Kullanıcı arabirimi tanımlarını içerir.

 ![Android ve Windows Phone 'de Xamarin uygulaması](../cross-platform/media/cross-plat-xamarin-build-1.png "Çapraz Plat Xamarin derleme 1")

 Bunu oluşturmak için şunları yapabilirsiniz:

- [Çözümünüzü ayarlama](#solution)

- [Paylaşılan veri hizmeti kodu yaz](#dataservice)

- [Android için tasarım kullanıcı arabirimi](#Android)

- [Windows Phone için tasarım kullanıcı arabirimi](#Windows)

- [Sonraki adımlar](#next)

> [!TIP]
> Bu proje için tam kaynak kodunu [GitHub 'daki mobil örnekler deposunda](https://github.com/xamarin/mobile-samples/tree/master/Weather)bulabilirsiniz.
>
> Zorluklarla karşılaşıyorsanız veya hatalarla karşılaşırsanız lütfen [forums.Xamarin.com](https://forums.xamarin.com/)adresindeki sorularınızı gönderin. Birçok hata, her platform için  [Xamarin sürüm notlarında](https://developer.xamarin.com/) açıklanan Xamarin 'in gerektirdiği en son SDK 'lara güncelleştirilerek çözülebilir.
>
> [!NOTE]
> Xamarin 'in geliştirici belgeleri aşağıda listelenen hem hızlı başlangıç hem de derinlemesine bakış bölümleri ile çeşitli izlenecek yollar sunar. Bu sayfaların tümünde, Visual Studio 'ya özgü izlenecek yolları görmek için sayfanın sağ üst kısmında "Visual Studio" öğesinin seçildiğinden emin olun.
>
> - Yerel UI ile Xamarin uygulamaları:
>
>   - [Merhaba, Android](https://developer.xamarin.com/guides/android/getting_started/hello,android/) (tek ekranlı basit uygulama)
>   - [Merhaba, Android multiscreen](https://developer.xamarin.com/guides/android/getting_started/hello,android_multiscreen/) (ekranlar arasında gezinle uygulama)
>   - [Android parçaları](/xamarin/android/platform/fragments/implementing-with-fragments/) Kılavuzu (diğer şeyler arasında ana/ayrıntı ekranları için kullanılır)
>   - [Hello, iOS](https://developer.xamarin.com/guides/ios/getting_started/hello,_iOS/)
>   - [Çok Ekranlı Hello, iOS](https://developer.xamarin.com/guides/ios/getting_started/hello,_iOS_multiscreen/)
>   - Xamarin. Forms ile Xamarin uygulamaları (paylaşılan kullanıcı arabirimi)
>
>   - [Hello, Xamarin.Forms](https://developer.xamarin.com/guides/cross-platform/xamarin-forms/getting-started/hello-xamarin-forms/quickstart/)
>   - [Hello, Xamarin.Forms Multiscreen](https://developer.xamarin.com/guides/cross-platform/xamarin-forms/getting-started/hello-xamarin-forms-multiscreen/)

## <a name="set-up-your-solution"></a><a name="solution"></a> Çözümünüzü ayarlama
 Bu adımlar, paylaşılan kod için PCL ve iki adet eklenen NuGet paketi içeren yerel kullanıcı arabirimine sahip bir Xamarin çözümü oluşturur.

1. Visual Studio 'da yeni bir **boş uygulama (yerel taşınabilir)** çözümü oluşturun ve bunu bir **hava uygulama**adıyla adlandırın. Bu şablonu, **Yerel taşınabilen** arama alanına girerek en kolay şekilde bulabilirsiniz.

    Bu yoksa, Xamarin 'i yüklemek veya Visual Studio 2015 özelliğini etkinleştirmek zorunda kalabilirsiniz. [Kurulum ve yükleme](../cross-platform/setup-and-install.md)bölümüne bakın.

2. Çözümü oluşturmak için Tamam ' a tıkladıktan sonra bir dizi bağımsız projeniz olacaktır:

   - **Dalgalı uygulama (taşınabilir)**: Xamarin. Forms ile kullanılan ortak iş mantığı ve Kullanıcı arabirimi kodu dahil olmak üzere platformlar arasında paylaşılan kod yazacağınız PCL.

   - **Dalgalı uygulama. DROID**: Yerel Android kodunu içeren proje. Bu, varsayılan başlangıç projesi olarak ayarlanır.

   - **Dalgalı uygulama. iOS**: Yerel iOS kodunu içeren proje.

   - **Dalgalı uygulama. WinPhone (Windows Phone 8,1)**: yerel Windows Phone kodunu içeren proje.

     Her yerel projede, karşılık gelen platform için yerel tasarımcıya erişiminiz vardır ve platforma özel ekranlar uygulayabilir.

3. **Newtonsoft.Js** ve NuGet paketini bir hava durumu veri hizmetinden alınan bilgileri işlemek IÇIN kullanacağınız PCL projesine ekleyin:

   - Çözüm Gezgini 'nde **Çözüm ' Katheruyg '** öğesine sağ tıklayın ve **çözüm Için NuGet Paketlerini Yönet..**. seçeneğini belirleyin.

        NuGet penceresinde, **Gözden** geçirme sekmesini seçin ve **Newtonsoft**için arama yapın.

   - **Newtonsoft.Js**seçin.

   - Pencerenin sağ tarafında, **dalgalı uygulama** projesini denetleyin (Bu, paketi yüklemeniz gereken tek projem olur).

   - **Sürüm** alanının **en son kararlı** sürüme ayarlandığından emin olun.

   - **Yükle**'ye tıklayın.

   - ![NuGet paketine Newtonsoft.Jsbulma ve yükleme](../cross-platform/media/crossplat-xamarin-formsguide-5.png "Çapraz Splat Xamarin FormsGuide 5")

4. **Microsoft.net. http** paketini bulmak ve yüklemek için 3. adımı yineleyin.

5. Çözümünüzü derleyin ve derleme hatası olmadığını doğrulayın.

## <a name="write-shared-data-service-code"></a><a name="dataservice"></a> Paylaşılan veri hizmeti kodu yaz
 **Hava uygulama (taşınabilir)** projesi, tüm platformlarda paylaşılan taşınabilir sınıf KITAPLıĞı (PCL) için kod yazacağınız yerdir. PCL, iOS, Android ve Windows Phone projeleri tarafından oluşturulan uygulama paketlerine otomatik olarak eklenir.

 Aşağıdaki adımlar, bu hava durumu hizmetine erişmek ve verileri depolamak için PCL 'e kod ekler:

1. Bu örneği çalıştırmak için, ilk olarak bir ücretsiz API anahtarına kaydolmanız gerekir [http://openweathermap.org/appid](https://openweathermap.org/appid) .

2. **Dalgalı uygulama** projesine sağ tıklayın ve **> Sınıf Ekle...** seçeneğini belirleyin. **Yeni öğe Ekle** iletişim kutusunda dosyayı **Weather.cs**olarak adlandırın. Bu sınıfı, hava durumu verileri hizmetinden veri depolamak için kullanacaksınız.

3. **Weather.cs** öğesinin tüm içeriğini aşağıdaki kodla değiştirin:

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

4. **DataService.cs** adlı PCL projesine, hava durumu VERI hizmetindeki JSON verilerini işlemek için kullanacağınız başka bir sınıf ekleyin.

5. **DataService.cs** öğesinin tüm içeriğini aşağıdaki kodla değiştirin:

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

6. Bir veri kümesi kodu ile bir sorgu dizesi oluşturan, hava durumu verileri hizmetini çağıran ve **Hava durumu** sınıfının bir örneğini dolduran Logic gibi paylaşılan iş mantığını YERLEŞTIRECEĞINIZ, PCL adlı **çekirdeğe** üçüncü bir sınıf ekleyin.

7. **Core.cs** içeriğini aşağıdaki kodla değiştirin:

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

                //Make sure developers running this sample replaced the API key
                if (key == "YOUR API KEY HERE")
                {
                    throw new ArgumentException("You must obtain an API key from openweathermap.org/appid and save it in the 'key' variable.");
                }

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

8. Kodunuzda *ANAHTARıNıZı burada* , 1. adımda elde ettiğiniz API anahtarıyla değiştirin (yine de çevresinde tırnak işareti olması gerekir).

9. Bunu kullanmayabilmemiz için PCL 'de MyClass.cs silin.

10. Kodun doğru olduğundan emin olmak için **dalgalı uygulama** PCL projesi oluşturun.

## <a name="design-ui-for-android"></a><a name="Android"></a> Android için tasarım kullanıcı arabirimi
 Şimdi Kullanıcı arabirimini tasarlayacağız, paylaşılan kodunuza bağlayacağız ve sonra uygulamayı çalıştıracağız.

### <a name="design-the-look-and-feel-of-your-app"></a>Uygulamanızın görünümünü tasarlama

1. **Çözüm Gezgini**, **gentherapp. DROID** > **kaynakları** > **Düzen** klasörünü genişletin ve **Main. axml**' yi açın. Bu, dosyayı görsel tasarımcıda açar. (Java ile ilgili bir hata görünürse, bu [blog gönderisine](https://forums.xamarin.com/discussion/32365/connection-to-the-layout-renderer-failed-in-xs-5-7-and-xamarinvs-3-9)bakın.)

    > [!TIP]
    > Projede birçok başka dosya vardır. Bu konunun kapsamı ötesinde, ancak bir Android projesinin yapısına biraz daha fazla bilgi almak istiyorsanız, xamarin.com adresindeki Merhaba Android konusunun [2. bölümünü](/xamarin/android/get-started/hello-android/hello-android-deepdive?pivots=windows) inceleyin.

2. Tasarımcıda görünen varsayılan düğmeyi seçin ve silin.

3. **> diğer Windows > araç kutusu**Ile araç kutusunu açın.

4. **Araç kutusundan**bir **RelativeLayout** denetimini tasarımcıya sürükleyin. Bu denetimi, diğer denetimler için bir üst kapsayıcı olarak kullanacaksınız.

    > [!TIP]
    > Herhangi bir zamanda düzen doğru şekilde görüntülenemeyebilir, dosyayı kaydedin ve yenileme için **Tasarım** ve **kaynak** sekmeleri arasında geçiş yapın.

5. **Özellikler** penceresinde, **Arkaplan** özelliğini (stil grubunda) olarak ayarlayın `#545454` .

6. **Araç kutusundan**, bir **TextView** denetimini **RelativeLayout** denetimine sürükleyin.

7. **Özellikler** penceresinde, bu özellikleri ayarlayın (note: Özellikler penceresi araç çubuğundaki sıralama düğmesini kullanarak listeyi alfabetik olarak sıralamanıza yardımcı olabilir):

    |Özellik|Değer|
    |--------------|-----------|
    |**metinleri**|**ZIP koduna göre ara**|
    |**id**|`@+id/ZipCodeSearchLabel`|
    |**layout_marginLeft**|`10dp`|
    |**textColor**|`@android:color/white`|
    |**Oluşturdu**|`bold`|

    > [!TIP]
    > Birçok özellik, seçebileceğiniz değerlerin açılan bir listesini içermediğine dikkat edin.  Verilen herhangi bir özellik için kullanılacak dize değerini tahmin etmek zor olabilir. Öneriler için, [R. attr](https://developer.android.com/reference/android/R.attr.html) sınıfı sayfasında bir özelliğin adını aramayı deneyin.
    >
    >  Ayrıca, hızlı bir Web araması genellikle [http://stackoverflow.com/](https://stackoverflow.com/) diğerlerinin aynı özelliği kullandığı bir sayfaya yol açar.

     Başvuru için, **kaynak** görünümüne geçerseniz, bu öğe için aşağıdaki kodu görmeniz gerekir:

    ```xml
    <TextView
        android:text="Search by Zip Code"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:id="@+id/ZipCodeSearchLabel"
        android:layout_centerVertical="true"
        android:layout_marginLeft="10dp"
        android:textColor="@android:color/white"
        android:textStyle="bold" />

    ```

8. **Araç kutusundan**, bir **TextView** denetimini **RelativeLayout** denetimine sürükleyin ve zipcodesearchlabel denetiminin altına yerleştirin. Bunu, yeni denetimi varolan denetimin uygun kenarına bırakarak yapabilirsiniz; Bu, tasarımcı 'nın bu şekilde yakınlaştırmasına yardımcı olur.

9. **Özellikler** penceresinde, aşağıdaki özellikleri ayarlayın:

    |Özellik|Değer|
    |--------------|-----------|
    |**metinleri**|**Posta Kodu**|
    |**id**|`@+id/ZipCodeLabel`|
    |**layout_marginLeft**|`10dp`|
    |**layout_marginTop**|`5dp`|

     **Kaynak** görünümündeki Kod şöyle görünmelidir:

    ```xml
    <TextView
        android:text="Zip Code"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_below="@id/ZipCodeSearchLabel"
        android:id="@+id/ZipCodeLabel"
        android:layout_marginTop="5dp"
        android:layout_marginLeft="10dp" />
    ```

10. **Araç kutusundan**bir **sayı** denetimini **RelativeLayout**üzerine sürükleyin, **ZIP kodu** etiketinin altına yerleştirin. Ardından aşağıdaki özellikleri ayarlayın:

    |Özellik|Değer|
    |--------------|-----------|
    |**id**|`@+id/zipCodeEntry`|
    |**layout_marginLeft**|`10dp`|
    |**layout_marginBottom**|`10dp`|
    |**Genişlik**|`165dp`|

     Yeniden, kod:

    ```xml
    <EditText
        android:inputType="number"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_below="@id/ZipCodeLabel"
        android:id="@+id/zipCodeEntry"
        android:layout_marginLeft="10dp"
        android:layout_marginBottom="10dp"
        android:width="165dp" />
    ```

11. **Araç kutusundan**, bir **düğmeyi** **RelativeLayout** denetimine sürükleyin ve zipcodeentry denetiminin sağına konumlandırın. Sonra bu özellikleri ayarlayın:

    |Özellik|Değer|
    |--------------|-----------|
    |**id**|`@+id/weatherBtn`|
    |**metinleri**|**Hava durumu Al**|
    |**layout_marginLeft**|`20dp`|
    |**layout_alignBottom**|`@id/zipCodeEntry`|
    |**Genişlik**|`165dp`|

    ```xml
    <Button    android:text="Get Weather"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_toRightOf="@id/zipCodeEntry"
        android:id="@+id/weatherBtn"
        android:layout_marginLeft="20dp"
        android:layout_alignBottom="@id/zipCodeEntry"
        android:width="165dp" />
    ```

12. Artık Android tasarımcısını kullanarak temel bir kullanıcı arabirimi oluşturmak için yeterli deneyimle karşılaşırsınız. Ayrıca, sayfanın. ASXML dosyasına doğrudan biçimlendirme ekleyerek bir kullanıcı arabirimi oluşturabilirsiniz. Kullanıcı arabiriminin geri kalanını oluşturmak için, tasarımcıda kaynak görünümüne geçiş yapın, ardından etiketin *altında* bulunan aşağıdaki biçimlendirmeyi geçmiş `</RelativeLayout>` (Evet, etiketin altında... Bu öğeler ReleativeLayout) içinde yer alır.

    ```xml
    <TextView
            android:text="Location"
            android:textAppearance="?android:attr/textAppearanceSmall"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/locationLabel"
            android:layout_marginLeft="10dp"
            android:layout_marginTop="10dp" />
        <TextView
            android:textAppearance="?android:attr/textAppearanceMedium"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/locationText"
            android:layout_marginLeft="20dp"
            android:layout_marginBottom="10dp" />
        <TextView
            android:text="Temperature"
            android:textAppearance="?android:attr/textAppearanceSmall"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/tempLabel"
            android:layout_marginLeft="10dp" />
        <TextView
            android:textAppearance="?android:attr/textAppearanceMedium"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/tempText"
            android:layout_marginBottom="10dp"
            android:layout_marginLeft="20dp" />
        <TextView
            android:text="Wind Speed"
            android:textAppearance="?android:attr/textAppearanceSmall"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/windLabel"
            android:layout_marginLeft="10dp" />
        <TextView
            android:textAppearance="?android:attr/textAppearanceMedium"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/windText"
            android:layout_marginBottom="10dp"
            android:layout_marginLeft="20dp" />
        <TextView
            android:text="Humidity"
            android:textAppearance="?android:attr/textAppearanceSmall"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/humidtyLabel"
            android:layout_marginLeft="10dp" />
        <TextView
            android:textAppearance="?android:attr/textAppearanceMedium"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/humidityText"
            android:layout_marginBottom="10dp"
            android:layout_marginLeft="20dp" />
        <TextView
            android:text="Visibility"
            android:textAppearance="?android:attr/textAppearanceSmall"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/visibilityLabel"
            android:layout_marginLeft="10dp" />
        <TextView
            android:textAppearance="?android:attr/textAppearanceMedium"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/visibilityText"
            android:layout_marginBottom="10dp"
            android:layout_marginLeft="20dp" />
        <TextView
            android:text="Time of Sunrise"
            android:textAppearance="?android:attr/textAppearanceSmall"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/sunriseLabel"
            android:layout_marginLeft="10dp" />
        <TextView
            android:textAppearance="?android:attr/textAppearanceMedium"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/sunriseText"
            android:layout_marginBottom="10dp"
            android:layout_marginLeft="20dp" />
        <TextView
            android:text="Time of Sunset"
            android:textAppearance="?android:attr/textAppearanceSmall"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/sunsetLabel"
            android:layout_marginLeft="10dp" />
        <TextView
            android:textAppearance="?android:attr/textAppearanceMedium"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/sunsetText"
            android:layout_marginBottom="10dp"
            android:layout_marginLeft="20dp" />

    ```

13. Dosyayı kaydedin ve **Tasarım** görünümüne geçin. Kullanıcı arabiriminizi aşağıdaki gibi görünmelidir:

     ![Android uygulaması için Kullanıcı arabirimi](../cross-platform/media/xamarin-androidui.png "Xamarin_AndroidUI")

14. **MainActivity.cs** açın ve daha önce kaldırılan varsayılan düğmeye başvuran *OnCreate* yöntemindeki satırları silin. Bitirdiğinizde kod aşağıdaki gibi görünmelidir:

    ```
    protected override void OnCreate (Bundle bundle)
    {
        base.OnCreate (bundle);

        // Set our view from the "main" layout resource
        SetContentView (Resource.Layout.Main);
    }
    ```

15. İşinizi denetlemek için Android projesi oluşturun. Derleme, **Resource.Designer.cs** dosyasına denetim kimliği eklediğine ve böylece, koddaki ada göre denetimlere başvurabilirsiniz.

### <a name="consume-your-shared-code"></a>Paylaşılan kodunuzu tüketme

1. Kod düzenleyicisinde **MainActivity.cs** dosyasını açın ve **WeatherApp** içeriğini aşağıdaki kodla değiştirin. Bu kod, `GetWeather` paylaşılan kodunuzda tanımladığınız yöntemi çağırır. Ardından, uygulamanın kullanıcı arabiriminde, bu yöntemden alınan verileri gösterir.

    ```csharp
    using System;
    using Android.App;
    using Android.Widget;
    using Android.OS;

    namespace WeatherApp.Droid
    {
        [Activity(Label = "Sample Weather App", MainLauncher = true, Icon = "@drawable/icon")]
        public class MainActivity : Activity
        {
            protected override void OnCreate(Bundle bundle)
            {
                base.OnCreate(bundle);

                SetContentView(Resource.Layout.Main);

                Button button = FindViewById<Button>(Resource.Id.weatherBtn);

                button.Click += Button_Click;
            }

            private async void Button_Click(object sender, EventArgs e)
            {
                EditText zipCodeEntry = FindViewById<EditText>(Resource.Id.zipCodeEntry);

                if (!String.IsNullOrEmpty(zipCodeEntry.Text))
                {
                    Weather weather = await Core.GetWeather(zipCodeEntry.Text);
                    FindViewById<TextView>(Resource.Id.locationText).Text = weather.Title;
                    FindViewById<TextView>(Resource.Id.tempText).Text = weather.Temperature;
                    FindViewById<TextView>(Resource.Id.windText).Text = weather.Wind;
                    FindViewById<TextView>(Resource.Id.visibilityText).Text = weather.Visibility;
                    FindViewById<TextView>(Resource.Id.humidityText).Text = weather.Humidity;
                    FindViewById<TextView>(Resource.Id.sunriseText).Text = weather.Sunrise;
                    FindViewById<TextView>(Resource.Id.sunsetText).Text = weather.Sunset;
                }
            }
        }
    }
    ```

### <a name="run-the-app-and-see-how-it-looks"></a>Uygulamayı çalıştırın ve nasıl göründüğünü görün

1. **Çözüm Gezgini**, **dalgalı uygulama. DROID** projesinin başlangıç projesi olarak ayarlandığından emin olun.

2. Uygun bir cihaz veya öykünücü hedefi seçin, sonra F5 tuşuna basarak uygulamayı başlatın.

3. Cihazda veya Öykünücüde, düzenleme kutusuna geçerli bir Birleşik Devletler posta kodu yazın (örneğin: 60601) ve **Hava durumu Al**' a basın. Bu bölge için hava durumu verileri daha sonra denetimlerde görüntülenir.

     ![Android ve Windows Phone için hava durumu uygulaması](../cross-platform/media/xamarin-getstarted-results.png "Xamarin_GetStarted_Results")

> [!TIP]
> Bu proje için tam kaynak kodu [GitHub 'daki mobil örnek depodadır](https://github.com/xamarin/mobile-samples/tree/master/Weather).

## <a name="design-ui-for-windows-phone"></a><a name="Windows"></a> Windows Phone için tasarım kullanıcı arabirimi
 Artık Windows Phone için Kullanıcı arabirimini tasarlayacağız, paylaşılan kodunuza bağlayacağız ve sonra uygulamayı çalıştıracağız.

### <a name="design-the-look-and-feel-of-your-app"></a>Uygulamanızın görünümünü tasarlama
 Bir Xamarin uygulamasında yerel Windows Phone UI tasarlama işlemi, başka bir yerel Windows Phone uygulamasından farklı değildir. Bu nedenle, tasarımcı 'yı nasıl kullanacağınızı öğrenmek için buradaki ayrıntılara gidemeyeceğiz. [Bunun için XAML Tasarımcısı kullanarak bir kullanıcı arabirimi oluşturma](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)bölümüne bakın.

 Bunun yerine, MainPage. xaml ' yi açmanız ve tüm XAML kodunu aşağıdaki gibi değiştirmeniz yeterlidir:

```xaml
<Page
    x:Class="WeatherApp.WinPhone.MainPage"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:WeatherApp.WinPhone"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    mc:Ignorable="d"
    Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">

    <Grid>
        <StackPanel HorizontalAlignment="Left" Height="40" Margin="10,0,0,0" VerticalAlignment="Top" Width="400">
            <TextBlock x:Name="pageTitle" Text="Weather App" FontSize="30" />
        </StackPanel>
        <StackPanel HorizontalAlignment="Left" Height="120" Margin="10,40,0,0" VerticalAlignment="Top" Width="400" Background="#FF545454">

            <TextBlock x:Name="zipCodeSearchLabel" TextWrapping="Wrap" Text="Search by Zip Code" FontSize="18" FontWeight="Bold" HorizontalAlignment="Left" Margin="10,10,0,0"/>
            <TextBlock x:Name="zipCodeLabel" TextWrapping="Wrap" Text="Zip Code" Margin="10,5,0,0" FontSize="14" Foreground="#FFA8A8A8"/>
            <StackPanel Orientation="Horizontal">
                <TextBox x:Name="zipCodeEntry" Margin="10,10,0,0" Text="" VerticalAlignment="Top" InputScope="Number" Width="165" />
                <Button x:Name="weatherBtn" Content="Get Weather" Width="165" Margin="20,0,0,0" Height="60" Click="GetWeatherButton_Click"/>
            </StackPanel>
        </StackPanel>
        <StackPanel Margin="10,175,0,0">
            <TextBlock x:Name="locationLabel" HorizontalAlignment="Left" FontSize="14" Foreground="#FFA8A8A8" TextWrapping="Wrap" Text="Location" VerticalAlignment="Top"/>
            <TextBlock x:Name="locationText" Margin="10,0,0,10" HorizontalAlignment="Left" FontSize="18" TextWrapping="Wrap" VerticalAlignment="Top"/>
            <TextBlock x:Name="tempLabel" HorizontalAlignment="Left" FontSize="14" Foreground="#FFA8A8A8" TextWrapping="Wrap" Text="Temperature" VerticalAlignment="Top"/>
            <TextBlock x:Name="tempText" Margin="10,0,0,10" HorizontalAlignment="Left" FontSize="18" TextWrapping="Wrap" VerticalAlignment="Top"/>
            <TextBlock x:Name="windLabel" HorizontalAlignment="Left" FontSize="14" Foreground="#FFA8A8A8" TextWrapping="Wrap" Text="Wind Speed" VerticalAlignment="Top"/>
            <TextBlock x:Name="windText" Margin="10,0,0,10" HorizontalAlignment="Left" FontSize="18" TextWrapping="Wrap" VerticalAlignment="Top"/>
            <TextBlock x:Name="humidityLabel" HorizontalAlignment="Left" FontSize="14" Foreground="#FFA8A8A8" TextWrapping="Wrap" Text="Humidity" VerticalAlignment="Top"/>
            <TextBlock x:Name="humidityText" Margin="10,0,0,10" HorizontalAlignment="Left" FontSize="18" TextWrapping="Wrap" VerticalAlignment="Top"/>
            <TextBlock x:Name="visibilityLabel" HorizontalAlignment="Left" FontSize="14" Foreground="#FFA8A8A8" TextWrapping="Wrap" Text="Temperature" VerticalAlignment="Top"/>
            <TextBlock x:Name="visibilityText" Margin="10,0,0,10" HorizontalAlignment="Left" FontSize="18" TextWrapping="Wrap" VerticalAlignment="Top"/>
            <TextBlock x:Name="sunriseLabel" HorizontalAlignment="Left" FontSize="14" Foreground="#FFA8A8A8" TextWrapping="Wrap" Text="Time of Sunriweatherse" VerticalAlignment="Top"/>
            <TextBlock x:Name="sunriseText" Margin="10,0,0,10" HorizontalAlignment="Left" FontSize="18" TextWrapping="Wrap" VerticalAlignment="Top"/>
            <TextBlock x:Name="sunsetLabel" HorizontalAlignment="Left" FontSize="14" Foreground="#FFA8A8A8" TextWrapping="Wrap" Text="Time of Sunset" VerticalAlignment="Top"/>
            <TextBlock x:Name="sunsetText" Margin="10,0,0,10" HorizontalAlignment="Left" FontSize="18" TextWrapping="Wrap" VerticalAlignment="Top"/>
        </StackPanel>
    </Grid>
</Page>
```

 Tasarım görünümünde, Kullanıcı arabiriminizi aşağıdaki gibi görünmelidir:

 ![Windows Phone uygulama kullanıcı arabirimi](../cross-platform/media/xamarin-winphone-finalui.png "Xamarin_WinPhone_FinalUI")

### <a name="consume-your-shared-code"></a>Paylaşılan kodunuzu tüketme

1. Tasarımcıda **Hava durumu Al** düğmesini seçin.

2. **Özellikler** penceresinde olay işleyicisi düğmesini (![Visual Studio olay işleyicileri simgesi](../cross-platform/media/blend-vs-eventhandlers-icon.png "blend_VS_EventHandlers_icon")) seçin.

     Bu simge, **Özellikler** penceresinin üst köşesinde görüntülenir.

3. **Click** olayının yanındaki **GETWEATHERBUTTON_CLICK**yazın ve ENTER tuşuna basın.

     Bu, adlı bir olay işleyicisi oluşturur `GetWeatherButton_Click` . Kod Düzenleyicisi açılır ve imlecinizi olay işleyicisi kod bloğunun içine koyar.  Note: ENTER tuşuna basıldığında düzenleyici açılmazsa, yalnızca olay adına çift tıklayın.

4. Bu olay işleyicisini aşağıdaki kodla değiştirin.

    ```csharp
    private async void GetWeatherButton_Click(object sender, RoutedEventArgs e)
    {
        if (!String.IsNullOrEmpty(zipCodeEntry.Text))
        {
            Weather weather = await Core.GetWeather(zipCodeEntry.Text);
            locationText.Text = weather.Title;
            tempText.Text = weather.Temperature;
            windText.Text = weather.Wind;
            visibilityText.Text = weather.Visibility;
            humidityText.Text = weather.Humidity;
            sunriseText.Text = weather.Sunrise;
            sunsetText.Text = weather.Sunset;

            weatherBtn.Content = "Search Again";
        }
    }
    ```

     Bu kod, `GetWeather` paylaşılan kodunuzda tanımladığınız yöntemi çağırır. Bu, Android uygulamanızda çağrın aynı yöntemidir. Bu kod ayrıca, uygulamanızın kullanıcı arabirimi denetimlerinde Bu yöntemden alınan verileri gösterir.

5. Açık olan MainPage.xaml.cs içinde, **OnNavigatedTo** yöntemi içindeki tüm kodu silin. Bu kod yalnızca MainPage. XAML içeriğini değiştirdiğimiz sırada kaldırılan varsayılan düğmeyi ele alır.

### <a name="run-the-app-and-see-how-it-looks"></a>Uygulamayı çalıştırın ve nasıl göründüğünü görün

1. **Çözüm Gezgini**' de, **dalgalı uygulama. WinPhone** projesini başlangıç projesi olarak ayarlayın.

2. F5 tuşuna basarak uygulamayı başlatın.

3. Windows Phone öykünücüsünde, düzenleme kutusuna geçerli bir Birleşik Devletler posta kodu yazın (örneğin: 60601) ve **Hava durumu Al**' a basın. Bu bölge için hava durumu verileri daha sonra denetimlerde görüntülenir.

     ![Çalışan uygulamanın Windows sürümü](../cross-platform/media/xamarin-getstarted-results-windows.png "Xamarin_GetStarted_Results_Windows")

> [!TIP]
> Bu proje için tam kaynak kodu [GitHub 'daki mobil örnek depodadır](https://github.com/xamarin/mobile-samples/tree/master/Weather).

## <a name="next-steps"></a><a name="next"></a> Sonraki adımlar
 **Çözüme iOS için Kullanıcı arabirimi ekleme**

 İOS için yerel UI ekleyerek bu örneği genişletin. Bunun için, yerel ağınızda Xcode ve Xamarin yüklü bir Mac 'e bağlanmanız gerekir. Bunu yaptıktan sonra doğrudan Visual Studio 'da iOS tasarımcısını kullanabilirsiniz. Tamamlanmış bir uygulama için [GitHub 'daki mobil örnekler deposuna](https://github.com/xamarin/mobile-samples/tree/master/Weather) bakın.

 Ayrıca, [Merhaba, iOS](/xamarin/ios/get-started/hello-ios/hello-ios-quickstart?pivots=windows) (Xamarin.com) açıklamasına bakın. Bu sayfada, doğru yönerge kümesinin görünmesi için xamarin.com üzerindeki sayfaların sağ üst köşesinde "Visual Studio" öğesinin seçili olduğundan emin olun.

 **Paylaşılan bir projeye platforma özel kod ekleme**

 PCL 'in bir kez derlenmesi ve platforma özgü her uygulama paketine dahil olması nedeniyle, bir PCL içindeki paylaşılan kod, platformdan bağımsız bir uygulamadır. Platforma özgü kodu yalıtmak için koşullu derleme kullanan paylaşılan kod yazmak isterseniz, *paylaşılan* bir proje kullanabilirsiniz. Daha ayrıntılı bilgi için bkz. [ODE Sharing seçenekleri](/xamarin/cross-platform/app-fundamentals/code-sharing) (Xamarin.com).

## <a name="see-also"></a>Ayrıca Bkz.
 [Xamarin geliştirici sitesi](/xamarin/) [Windows Dev Center](https://dev.windows.com/en-us) [Swift ve C# hızlı başvuru poster](https://aka.ms/scposter)
