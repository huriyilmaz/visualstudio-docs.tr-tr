---
title: Xamarin kullanılarak yerel UI ile uygulamalar oluşturun
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: tgt-pltfrm-cross-plat
ms.topic: conceptual
ms.assetid: 30f137e6-595d-4ce7-b8f5-415b07c1caa2
caps.latest.revision: 33
ms.author: crdun
manager: crdun
ms.openlocfilehash: 7a0284ab6b8d2e89e1c0129c2bc98fb486918f90
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297916"
---
# <a name="build-apps-with-native-ui-using-xamarin-in-visual-studio"></a>Visual Studio’da Xamarin kullanarak yerel kullanıcı arabirimi ile uygulama oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[Xamarin ortamınızı](../cross-platform/verify-your-xamarin-environment.md) [Kurulum ve](../cross-platform/setup-and-install.md) doğrulama adımlarını tamamladıktan sonra Bu izlenecek yol, yerel kullanıcı arabirimi katmanları ile temel bir Xamarin uygulamasının (aşağıda gösterilmiştir) nasıl oluşturulacağını gösterir. Yerel UI ile paylaşılan kodun bir taşınabilir sınıf kitaplığı (PCL) yer alıyor ve ayrı bir platform projeleri kullanıcı Arabirimi tanımları içerir.

 ![Android ve Windows Phone 'de Xamarin uygulaması](../cross-platform/media/cross-plat-xamarin-build-1.png "Çapraz Plat Xamarin derleme 1")

 Derlemek için bu işlemleri yapmanız:

- [Çözümünüzü ayarlama](#solution)

- [Paylaşılan veri hizmeti kodu yaz](#dataservice)

- [Android için tasarım kullanıcı arabirimi](#Android)

- [Windows Phone için tasarım kullanıcı arabirimi](#Windows)

- [Sonraki adımlar](#next)

> [!TIP]
> Bu proje için tam kaynak kodunu [GitHub 'daki mobil örnekler deposunda](https://github.com/xamarin/mobile-samples/tree/master/Weather)bulabilirsiniz.
>
> Zorluklarla karşılaşıyorsanız veya hatalarla karşılaşırsanız lütfen [forums.Xamarin.com](https://forums.xamarin.com/)adresindeki sorularınızı gönderin. Birçok hata, her platform için [Xamarin sürüm notlarında](https://developer.xamarin.com/) açıklanan Xamarin 'in gerektirdiği en son SDK 'lara güncelleştirilerek çözülebilir.
>
> [!NOTE]
> Xamarin Geliştirici belgeleri, aşağıda listelenen birkaç izlenecek yollar hem hızlı başlangıç hem de yakından bölümleri ile de sunar. Tüm bu sayfalarda "Visual Studio" Visual Studio özel Kılavuzlar görmek için sağ üst köşede sayfanın seçili olduğundan emin olun.
>
> - Xamarin uygulamaları yerel UI ile:
>
>   - [Merhaba, Android](https://developer.xamarin.com/guides/android/getting_started/hello,android/) (tek ekranlı basit uygulama)
>   - [Merhaba, Android multiscreen](https://developer.xamarin.com/guides/android/getting_started/hello,android_multiscreen/) (ekranlar arasında gezinle uygulama)
>   - [Android parçaları](https://docs.microsoft.com/xamarin/android/platform/fragments/implementing-with-fragments/) Kılavuzu (diğer şeyler arasında ana/ayrıntı ekranları için kullanılır)
>   - [Hello, iOS](https://developer.xamarin.com/guides/ios/getting_started/hello,_iOS/)
>   - [Çok Ekranlı Hello, iOS ](https://developer.xamarin.com/guides/ios/getting_started/hello,_iOS_multiscreen/)
>   - Xamarin.Forms (paylaşılan UI) ile Xamarin uygulamaları
>
>   - [Hello, Xamarin.Forms](https://developer.xamarin.com/guides/cross-platform/xamarin-forms/getting-started/hello-xamarin-forms/quickstart/)
>   - [Hello, Xamarin.Forms Multiscreen](https://developer.xamarin.com/guides/cross-platform/xamarin-forms/getting-started/hello-xamarin-forms-multiscreen/)

## <a name="solution"></a>Çözümünüzü ayarlama
 Bu adımlar paylaşılan kod için bir PCL ve iki eklenen NuGet paketi içeren yerel UI ile bir Xamarin çözümü oluşturun.

1. Visual Studio 'da yeni bir **boş uygulama (yerel taşınabilir)** çözümü oluşturun ve bunu bir **hava uygulama**adıyla adlandırın. Bu şablonu, **Yerel taşınabilen** arama alanına girerek en kolay şekilde bulabilirsiniz.

    Bu yoksa, Xamarin 'i yüklemek veya Visual Studio 2015 özelliğini etkinleştirmek zorunda kalabilirsiniz. [Kurulum ve yükleme](../cross-platform/setup-and-install.md)bölümüne bakın.

2. Çözümü oluşturmak için Tamam'a tıkladıktan sonra bir dizi ayrı projeler gerekir:

   - **Dalgalı uygulama (taşınabilir)** : Xamarin. Forms ile kullanılan ortak iş mantığı ve Kullanıcı arabirimi kodu dahil olmak üzere platformlar arasında paylaşılan kod yazacağınız PCL.

   - **Dalgalı uygulama. DROID**: Yerel Android kodunu içeren proje. Bu, varsayılan başlangıç projesi olarak ayarlanır.

   - **Dalgalı uygulama. iOS**: Yerel iOS kodunu içeren proje.

   - **Dalgalı uygulama. WinPhone (Windows Phone 8,1)** : yerel Windows Phone kodunu içeren proje.

     Her yerel proje içinde karşılık gelen bir platform için yerel Tasarımcı erişimi vardır ve platform belirli ekranları uygulayabilirsiniz.

3. **Newtonsoft. JSON** ve NuGet paketini bir hava durumu veri hizmetinden alınan bilgileri işlemek IÇIN kullanacağınız PCL projesine ekleyin:

   - Çözüm Gezgini 'nde **Çözüm ' Katheruyg '** öğesine sağ tıklayın ve **çözüm Için NuGet Paketlerini Yönet..** . seçeneğini belirleyin.

        NuGet penceresinde, **Gözden** geçirme sekmesini seçin ve **Newtonsoft**için arama yapın.

   - **Newtonsoft. JSON**öğesini seçin.

   - Pencerenin sağ tarafında, **dalgalı uygulama** projesini denetleyin (Bu, paketi yüklemeniz gereken tek projem olur).

   - **Sürüm** alanının **en son kararlı** sürüme ayarlandığından emin olun.

   - **Yükle**'ye tıklayın.

   - ![Newtonsoft. JSON NuGet paketini bulma ve yükleme](../cross-platform/media/crossplat-xamarin-formsguide-5.png "Çapraz Splat Xamarin FormsGuide 5")

4. **Microsoft.net. http** paketini bulmak ve yüklemek için 3. adımı yineleyin.

5. Çözümünüzü oluşturun ve herhangi bir yapı hatası olmadığını doğrulayın.

## <a name="dataservice"></a>Paylaşılan veri hizmeti kodu yaz
 **Hava uygulama (taşınabilir)** projesi, tüm platformlarda paylaşılan taşınabilir sınıf KITAPLıĞı (PCL) için kod yazacağınız yerdir. PCL otomatik olarak derlenmiş iOS, Android ve Windows Phone uygulama paketleri dahil edilir.

 Aşağıdaki adımlar bu durumda, hava durumu hizmetinden veri depolamak ve erişmek için PCL kodu ekleyin:

1. Bu örneği çalıştırmak için, ilk olarak [http://openweathermap.org/appid](https://openweathermap.org/appid)BIR ücretsiz API anahtarına kaydolmanız gerekir.

2. **Dalgalı uygulama** projesine sağ tıklayın ve **> Sınıf Ekle...** seçeneğini belirleyin. **Yeni öğe Ekle** iletişim kutusunda dosyayı **Weather.cs**olarak adlandırın. Bu sınıf, hava durumu verileri hizmetten alınan verileri depolamak için kullanacaksınız.

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

9. Biz bunu Loaded MyClass.cs PCL içinde silin.

10. Kodun doğru olduğundan emin olmak için **dalgalı uygulama** PCL projesi oluşturun.

## <a name="Android"></a>Android için tasarım kullanıcı arabirimi
 Şimdi biz kullanıcı arabirimini tasarlayabileceğiniz paylaşılan kodunuza bağlayın ve sonra uygulamayı çalıştırın.

### <a name="design-the-look-and-feel-of-your-app"></a>Tasarım görünümü uygulama

1. **Çözüm Gezgini**, **dalgalı uygulama. DROID**>**kaynakları**>**Düzen** klasörünü genişletin ve **Main. axml**' yi açın. Bu dosya Görsel tasarımcıda açılır. (Java ile ilgili bir hata görünürse, bu [blog gönderisine](https://forums.xamarin.com/discussion/32365/connection-to-the-layout-renderer-failed-in-xs-5-7-and-xamarinvs-3-9)bakın.)

    > [!TIP]
    > Projede diğer birçok dosyası vardır. Bu konunun kapsamı ötesinde, ancak bir Android projesinin yapısına biraz daha fazla bilgi almak istiyorsanız, xamarin.com adresindeki Merhaba Android konusunun [2. bölümünü](https://docs.microsoft.com/xamarin/android/get-started/hello-android/hello-android-deepdive?pivots=windows) inceleyin.

2. Seçip Tasarımcısı'nda görüntülenen varsayılan düğme silin.

3. **> diğer Windows > araç kutusu**Ile araç kutusunu açın.

4. **Araç kutusundan**bir **RelativeLayout** denetimini tasarımcıya sürükleyin. Bu denetim, diğer denetimler için üst kapsayıcı olarak kullanacaksınız.

    > [!TIP]
    > Herhangi bir zamanda düzen doğru şekilde görüntülenemeyebilir, dosyayı kaydedin ve yenileme için **Tasarım** ve **kaynak** sekmeleri arasında geçiş yapın.

5. **Özellikler** penceresinde, **arka plan** özelliğini (stil grubunda) `#545454`olarak ayarlayın.

6. **Araç kutusundan**, bir **TextView** denetimini **RelativeLayout** denetimine sürükleyin.

7. **Özellikler** penceresinde, bu özellikleri ayarlayın (note: Özellikler penceresi araç çubuğundaki sıralama düğmesini kullanarak listeyi alfabetik olarak sıralamanıza yardımcı olabilir):

    |Özellik|Value|
    |--------------|-----------|
    |**metinleri**|**ZIP koduna göre ara**|
    |**id**|`@+id/ZipCodeSearchLabel`|
    |**layout_marginLeft**|`10dp`|
    |**textColor**|`@android:color/white`|
    |**Oluşturdu**|`bold`|

    > [!TIP]
    > Pek çok özellik seçebileceğiniz değerler, aşağı açılan listesini içermeyen dikkat edin.  Belirli bir özellik için kullanılacak dize değeri tahmin etmek zor olabilir. Öneriler için, [R. attr](https://developer.android.com/reference/android/R.attr.html) sınıfı sayfasında bir özelliğin adını aramayı deneyin.
    >
    >  Ayrıca, hızlı bir Web araması genellikle diğerlerinin aynı özelliği kullandığı [http://stackoverflow.com/](https://stackoverflow.com/) bir sayfaya yönlendirir.

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

8. **Araç kutusundan**, bir **TextView** denetimini **RelativeLayout** denetimine sürükleyin ve zipcodesearchlabel denetiminin altına yerleştirin. Bunun için yeni denetimi varolan bir denetimi uygun kenarında bırakarak; Bunun için biraz tasarımcıda yakınlaştırmak için yardımcı olur.

9. **Özellikler** penceresinde, aşağıdaki özellikleri ayarlayın:

    |Özellik|Value|
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

    |Özellik|Value|
    |--------------|-----------|
    |**id**|`@+id/zipCodeEntry`|
    |**layout_marginLeft**|`10dp`|
    |**layout_marginBottom**|`10dp`|
    |**Genişlik**|`165dp`|

     Kodu yeniden:

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

11. **Araç kutusundan**, bir **düğmeyi** **RelativeLayout** denetimine sürükleyin ve zipcodeentry denetiminin sağına konumlandırın. Bu özellikleri ayarlayın:

    |Özellik|Value|
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

12. Artık Android designer kullanarak temel bir kullanıcı Arabirimi oluşturmak için yeterli bir deneyimi vardır. Biçimlendirme doğrudan sayfanın .asxml dosyasına ekleyerek, bir kullanıcı Arabirimi de oluşturabilirsiniz. Kullanıcı arabiriminin geri kalanını oluşturmak için, tasarımcıda kaynak görünümüne geçin ve sonra `</RelativeLayout>` etiketinin *altında* aşağıdaki biçimlendirmeyi geçmiş (Evet, etiketin altında... Bu öğeler ReleativeLayout) içinde yer alır.

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

13. Dosyayı kaydedin ve **Tasarım** görünümüne geçin. Kullanıcı Arabirimi aşağıdaki gibi görünmelidir:

     ![Android uygulaması için Kullanıcı arabirimi](../cross-platform/media/xamarin-androidui.png "Xamarin_AndroidUI")

14. **MainActivity.cs** açın ve daha önce kaldırılan varsayılan düğmeye başvuran *OnCreate* yöntemindeki satırları silin. İşiniz bittiğinde, kod şu şekilde görünmelidir:

    ```
    protected override void OnCreate (Bundle bundle)
    {
        base.OnCreate (bundle);

        // Set our view from the "main" layout resource
        SetContentView (Resource.Layout.Main);
    }
    ```

15. İş kontrol etmek için Android projesi oluşturun. Derleme, **Resource.Designer.cs** dosyasına denetim kimliği eklediğine ve böylece, koddaki ada göre denetimlere başvurabilirsiniz.

### <a name="consume-your-shared-code"></a>Paylaşılan kod kullanma

1. Kod düzenleyicisinde **MainActivity.cs** dosyasını açın ve içeriğini aşağıdaki kodla değiştirin. Bu kod, paylaşılan kodunuzda tanımladığınız `GetWeather` yöntemini çağırır. Ardından kullanıcı Arabiriminde uygulamanın Bu yöntemden alınan verileri gösterir.

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

### <a name="run-the-app-and-see-how-it-looks"></a>Uygulamayı çalıştırın ve nasıl göründüğüne bakın

1. **Çözüm Gezgini**, **dalgalı uygulama. DROID** projesinin başlangıç projesi olarak ayarlandığından emin olun.

2. Bir uygun cihaz veya öykünücü hedef seçin ve ardından F5 tuşuna basarak uygulamayı başlatın.

3. Cihazda veya Öykünücüde, düzenleme kutusuna geçerli bir Birleşik Devletler posta kodu yazın (örneğin: 60601) ve **Hava durumu Al**' a basın. Bu bölge için hava durumu verileri, ardından denetimleri görünür.

     ![Android ve Windows Phone için hava durumu uygulaması](../cross-platform/media/xamarin-getstarted-results.png "Xamarin_GetStarted_Results")

> [!TIP]
> Bu proje için tam kaynak kodu [GitHub 'daki mobil örnek depodadır](https://github.com/xamarin/mobile-samples/tree/master/Weather).

## <a name="Windows"></a>Windows Phone için tasarım kullanıcı arabirimi
 Şimdi biz Windows Phone için kullanıcı arabirimini tasarlayabileceğiniz paylaşılan kodunuza bağlayın ve sonra uygulamayı çalıştırın.

### <a name="design-the-look-and-feel-of-your-app"></a>Tasarım görünümü uygulama
 Yerel Windows Phone kullanıcı Arabiriminde bir Xamarin uygulaması tasarlama işlemi herhangi diğer yerel Windows Phone uygulamasından farklı değildir. Bu nedenle, biz ayrıntıları tasarımcıyı nasıl kullanacağınızı, burada gitmiyor. [Bunun için XAML Tasarımcısı kullanarak bir kullanıcı arabirimi oluşturma](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)bölümüne bakın.

 Bunun yerine, basitçe mainpage.XAML dosyasını açın ve tüm XAML kodu aşağıdakiyle değiştirin:

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

 Tasarım görünümünde, kullanıcı Arabirimi aşağıdaki gibi görünmelidir:

 ![Windows Phone uygulama kullanıcı arabirimi](../cross-platform/media/xamarin-winphone-finalui.png "Xamarin_WinPhone_FinalUI")

### <a name="consume-your-shared-code"></a>Paylaşılan kod kullanma

1. Tasarımcıda **Hava durumu Al** düğmesini seçin.

2. **Özellikler** penceresinde olay işleyicisi düğmesini (![Visual Studio olay işleyicileri simgesi](../cross-platform/media/blend-vs-eventhandlers-icon.png "blend_VS_EventHandlers_icon")) seçin.

     Bu simge, **Özellikler** penceresinin üst köşesinde görüntülenir.

3. **Click** olayının yanındaki **GETWEATHERBUTTON_CLICK**yazın ve ENTER tuşuna basın.

     Bu, `GetWeatherButton_Click`adlı bir olay işleyicisi oluşturur. Kod Düzenleyicisi açılır ve imlecinizi olay işleyicisine kod bloğunun içine yerleştirir.  Not: düzenleyicide ENTER tuşuna basıldığında açık değilse, yalnızca olay adına çift tıklayın.

4. Bu olay işleyicisi aşağıdaki kodla değiştirin.

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

     Bu kod, paylaşılan kodunuzda tanımladığınız `GetWeather` yöntemini çağırır. Bu Android uygulamanızda çağrılan yöntem ile aynıdır. Bu kod Ayrıca, uygulamanızın kullanıcı Arabirimi denetimleri yönteminde alınan verileri gösterir.

5. Açık olan MainPage.xaml.cs içinde, **OnNavigatedTo** yöntemi içindeki tüm kodu silin. Bu kod, sadece biz MainPage.xaml içeriği değiştirildiğinde kaldırılan varsayılan düğme işlenir.

### <a name="run-the-app-and-see-how-it-looks"></a>Uygulamayı çalıştırın ve nasıl göründüğüne bakın

1. **Çözüm Gezgini**' de, **dalgalı uygulama. WinPhone** projesini başlangıç projesi olarak ayarlayın.

2. F5 tuşuna basarak uygulamayı başlatın.

3. Windows Phone öykünücüsünde, düzenleme kutusuna geçerli bir Birleşik Devletler posta kodu yazın (örneğin: 60601) ve **Hava durumu Al**' a basın. Bu bölge için hava durumu verileri, ardından denetimleri görünür.

     ![Çalışan uygulamanın Windows sürümü](../cross-platform/media/xamarin-getstarted-results-windows.png "Xamarin_GetStarted_Results_Windows")

> [!TIP]
> Bu proje için tam kaynak kodu [GitHub 'daki mobil örnek depodadır](https://github.com/xamarin/mobile-samples/tree/master/Weather).

## <a name="next"></a> Sonraki adımlar
 **Çözüme iOS için Kullanıcı arabirimi ekleme**

 Bu örnek, iOS için yerel UI ekleyerek genişletin. Bunun için yerel ağınızda Xcode sahip bir mac'e bağlanmanız gerekir ve Xamarin yüklü. Bunu yaptığınızda, doğrudan Visual Studio'da iOS Tasarımcısı'nı kullanabilirsiniz. Tamamlanmış bir uygulama için [GitHub 'daki mobil örnekler deposuna](https://github.com/xamarin/mobile-samples/tree/master/Weather) bakın.

 Ayrıca, [Merhaba, iOS](https://docs.microsoft.com/xamarin/ios/get-started/hello-ios/hello-ios-quickstart?pivots=windows) (Xamarin.com) açıklamasına bakın. Yönerge kümesini doğru görünür, bu sayfada emin "Visual Studio" Not sağ üst köşesinde sayfaları xamarin.com üzerinde seçilir.

 **Paylaşılan bir projeye platforma özel kod ekleme**

 PCL kez derlenir ve her platforma özgü uygulama paketinde bir PCL paylaşılan kodu platformdan bağımsız olmasıdır. Platforma özgü kodu yalıtmak için koşullu derleme kullanan paylaşılan kod yazmak isterseniz, *paylaşılan* bir proje kullanabilirsiniz. Daha ayrıntılı bilgi için bkz. [ODE Sharing seçenekleri](https://docs.microsoft.com/xamarin/cross-platform/app-fundamentals/code-sharing) (Xamarin.com).

## <a name="see-also"></a>Ayrıca Bkz.
 [Xamarin geliştirici sitesi](https://docs.microsoft.com/xamarin/) [Windows Dev Center](https://dev.windows.com/en-us) [Swift ve C# hızlı başvuru poster](https://aka.ms/scposter)
