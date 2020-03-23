---
title: Unity ile oyun oluşturmaya başlama
description: Mac için Unity ve Visual Studio ile başlarken
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/20/2019
ms.technology: vs-ide-general
ms.assetid: D07FA43B-9D18-4DFA-8343-CD538FAD84DB
ms.openlocfilehash: c25df777a9af10859c70741a78c880a57c6f5b8e
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "74984800"
---
# <a name="getting-started-building-games-with-unity-in-visual-studio-for-mac"></a>Mac için Visual Studio'da Unity ile oyun oluşturmaya başlarken

Unity, C#'da oyun geliştirmenizi sağlayan bir oyun motorudur. Bu izlik, Unity ortamının yanı sıra Mac için Visual Studio ve Unity eklentisi için Mac Tools için Visual Studio'yu kullanarak Unity oyunları geliştirmeye ve hata ayıklamaya nasıl başlayıp başlatılasınız gösterir.

Visual Studio for Mac Tools for Unity, Visual Studio for Mac ile yüklenen ücretsiz bir uzantıdır. Unity geliştiricilerin, mükemmel IntelliSense desteği, hata ayıklama özellikleri ve daha fazlası dahil olmak üzere Visual Studio for Mac'in üretkenlik özelliklerinden yararlanmasını sağlar.

## <a name="objectives"></a>Amaçlar

> [!div class="checklist"]
> * Mac için Visual Studio ile Birlik geliştirme hakkında bilgi edinin

## <a name="prerequisites"></a>Önkoşullar

- Mac için Visual[https://www.visualstudio.com/vs/mac](https://www.visualstudio.com/vs/visual-studio-mac)Studio ( )
- Unity 5.6.1 Personal Edition[https://store.unity.com](https://store.unity.com/)veya üstü (, çalıştırmak için unity.com bir hesap gerektirir)

## <a name="intended-audience"></a>Hedef Kitle

Derin deneyim gerekli olmasa da, bu laboratuvar C # aşina geliştiriciler için tasarlanmıştır.

## <a name="task-1-creating-a-basic-unity-project"></a>Görev 1: Temel bir Birlik projesi oluşturma

1. **Birlik**başlatın. İstenirse oturum açın.

2. **Yeni'yi**tıklatın.

    ![Birlik içinde yeni düğme](media/unity-image1.png)

3. Proje **adını** **"UnityLab"** olarak ayarlayın ve **3D**seçin. **Proje Oluştur'u**tıklatın.

    ![yeni proje ekranı oluşturma](media/unity-image2.png)

4. Şimdi varsayılan Unity arabirimine bakıyorsunuz. Soldaki oyun nesneleri ile sahne hiyerarşisi, ortada gösterilen boş sahnenin 3D görünümü, alt kısmında bir proje dosyaları bölmesi ve sağda denetçi ve hizmetler vardır. Tabii ki, bundan çok daha fazlası var, ama bunlar daha önemli bileşenlerden birkaçı.

    ![boş birlik arayüzü](media/unity-image3.png)

5. Unity'ye yeni giren geliştiriciler için, uygulamanızda çalışan her şey bir **sahne**bağlamında var olacaktır. Sahne dosyası, geçerli sahne ve özellikleri için projede kullanılan kaynaklar hakkında her türlü meta veri içeren tek bir dosyadır. Uygulamanızı bir platform için paketlediğinizde, ortaya çıkan uygulama bir veya daha fazla sahnenin yanı sıra eklediğiniz platforma bağlı kodlardan oluşan bir koleksiyon haline gelir. Bir projede istediğiniz kadar sahne niz olabilir.

6. Yeni sahne sadece bir kamera ve bir yön ışığı vardır. Bir sahne, her şeyin görünür olması için bir **kamera** ve duyulabilir bir şey için bir **Ses Dinleyicisi** gerektirir. Bu bileşenler bir **GameObject'e**eklenir.

7. **Hiyerarşi** bölmesinden **Ana Kamera** nesnesini seçin.

    ![hiyerarşi bölmesinde vurgulanan ana kamera nesnesi](media/unity-image4.png)

8. Özelliklerini gözden geçirmek için pencerenin sağ tarafından **Denetçi** bölmesini seçin. Kamera özellikleri dönüşüm bilgileri, arka plan, projeksiyon türü, görüş alanı ve benzeri içerir. Ses Dinleyicisi bileşeni de varsayılan olarak eklenmiştir ve bu da kameraya bağlı sanal bir mikrofondan sahne sesini işler.

    ![denetçi bölmesi](media/unity-image5.png)

9. Yön **Işığı** nesnesini seçin. Bu, gölgeli gibi bileşenlerin nesneleri nasıl işiteceklerini bilmesi için sahneye ışık sağlar.

    ![yön ışığı nesnesi vurgulanır](media/unity-image6.png)

10. Tür, renk, yoğunluk, gölge türü ve benzeri ortak aydınlatma özelliklerini içerdiğini görmek için **Denetçi'yi** kullanın.

    ![denetçi bölmesindeki özelliklere bakmak](media/unity-image7.png)

11. Unity'deki projelerin Mac'teki meslektaşları için Visual Studio'larından biraz farklı olduğunu belirtmek önemlidir. Alttaki **Proje** sekmesinde, **Varlıklar** klasörüne sağ tıklayın ve **Finder'da Göster'i**seçin.

    ![bulucu bağlamında eylem ortaya](media/unity-image8.png)

12. Projeler, gördüğünüz gibi **Varlıklar,** **Kitaplık,** **Proje Ayarları**ve **Geçici** klasörler içerir. Ancak, arabirimde görünen tek kişi **Varlıklar** klasörüdür. **Kitaplık** klasörü, içe aktarılan varlıklar için yerel önbellektir; varlıklar için tüm meta verileri tutar. **ProjectSettings** klasörü yapılandırabileceğiniz ayarları depolar. **Geçici** klasör, yapı işlemi sırasında Mono ve Unity'den gelen geçici dosyalar için kullanılır. Mac için Visual Studio'da açabileceğiniz bir çözüm dosyası da vardır **(UnityLab.sln** burada).

    ![bulucu varlıklar](media/unity-image9.png)

13. **Bulucu** penceresini kapatın ve **Unity'ye**dönün.

14. **Varlıklar** klasörü tüm varlıklarınızı içerir-sanat, kod, ses, vb. Şu anda boş, ama projenize getirdiğiniz her dosya buraya gidiyor. Bu her zaman **Unity Editor'daki**üst düzey klasördür. Ama her zaman eklemek ve Unity arayüzü (veya Mac için Visual Studio) ve doğrudan dosya sistemi üzerinden asla dosyaları kaldırmak.

    ![unity varlıklar klasörü](media/unity-image10.png)

15. **GameObject,** modeller, ışıklar, parçacık sistemleri ve benzeri dahil olmak üzere hemen hemen her şey bu türden türetilmiştir gibi Unity geliştirme merkezidir. **GameObject > 3D Object > Cube** menüsü nden sahneye yeni bir **Küp** nesnesi ekleyin.

    ![sahnede küp nesne](media/unity-image11.png)

16. Yeni **GameObject'in** özelliklerine hızlıca bir göz atın ve bir adı, etiketi, katmanı ve dönüşümü olduğunu görün. Bu özellikler tüm **GameObjects**için ortak. Buna ek olarak, kafes filtresi, kutu çarpıştırıcısı ve işleyici gibi gerekli işlevselliği sağlamak için **Küp'e** birkaç bileşen eklenmiştir.

    ![oyun nesne özellikleri](media/unity-image12.png)

17. Varsayılan olarak **"Küp"** adını taşıyan **Küp** nesnesini **"Düşman"** olarak yeniden adlandırın. Değişikliği kaydetmek için **Enter** tuşuna bastığından emin olun. Bu bizim basit oyunda düşman küp ü olacak.

    ![küp nesne yeniden adlandırma özelliği](media/unity-image13.png)

18. Yukarıdaki işlemi kullanarak sahneye başka bir **Küp** nesnesi ekleyin ve bu bir **"Player"** adını.

    ![ikinci küp nesnesi yeniden adlandırma](media/unity-image14.png)

19. Oyuncu nesnesini **"Player"** olarak da etiketle (bkz. isim alanının hemen altındaki **Etiket** açılır denetimi). Bunu düşman senaryosunda kullanarak oyuncu oyun nesnesini bulmaya yardımcı olacağız.

    ![oyuncu nesnesini etiketleme](media/unity-image15.png)

20. **Sahne** görünümünde, fareyi kullanarak oyuncu nesnesini Z ekseni boyunca düşman nesnesinden uzaklaştırın. Küpü **kırmızı** paneli ile **mavi** çizgiye doğru seçip sürükleyerek Z ekseni boyunca hareket edebilirsiniz. Küp 3B boşlukta yaşadığından, ancak her seferinde yalnızca 2B olarak sürüklenebildiği için, sürüklediğiniz eksen özellikle önemlidir.

    ![küpü gösteren sahne görünümü](media/unity-image16.png)

21. Küpü eksen boyunca aşağı ve sağa doğru hareket ettirin. Bu, **Denetçi'deki** **Transform.Position** özelliğini güncelleştirir. Laboratuvarda daha sonraki adımları kolaylaştırmak için burada gösterilene benzer bir konuma sürüklemeyi unutmayın.

    ![eksen boyunca bir küp taşıma](media/unity-image17.png)

22. Şimdi oyuncu takip böylece düşman mantığı sürücü bazı kod ekleyebilirsiniz. **Proje** defterindeki **Varlıklar** klasörüne sağ tıklayın ve **C# Komut Dosyası > oluştur'u**seçin.

    ![C# komut dosyası bağlam ı eylem](media/unity-image18.png)

23. Yeni C# komut dosyasına **"EnemyAI"** adını söyle.

    ![C# betiği](media/unity-image19.png)

24. Oyun nesnelerine komut dosyası eklemek için yeni oluşturulan komut dosyasını **Hiyerarşi** bölmesinde **Düşman** nesnesine sürükleyin. Şimdi bu nesne bu komut dosyasının davranışlarını kullanır.

    ![oyun nesnesine komut dosyası eklemeyi vurgulama](media/unity-image20.png)

25. Geçerli sahneyi kaydetmek için **Dosya > Sahneleri Kaydet'i** seçin. Adını **"MyScene"** olarak adlandır.

## <a name="task-2-working-with-visual-studio-for-mac-tools-for-unity"></a>Görev 2: Birlik için Mac Tools için Visual Studio ile çalışma

1. C# kodunu yeniden kullanmanın en iyi yolu Mac için Visual Studio kullanmaktır. Varsayılan işleyicisi olarak Mac için Visual Studio'u kullanmak üzere Birlik'i yapılandırabilirsiniz. **Tercihler > Birlik'i**seçin.

2. Dış **Araçlar** sekmesini seçin. Harici **Komut Dosyası Düzenleyicisi** açılır tarafından, **Gözat'ı** seçin ve **Uygulamalar/Visual Studio.app'ı**seçin. Alternatif olarak, zaten bir **Visual Studio** seçeneği varsa, sadece seçin.

    ![tercihlerde dış araçlar sekmesi](media/unity-image21.png)

3. Unity artık komut dosyası düzenlemesi **için Mac için Visual Studio'yu** kullanacak şekilde yapılandırılmıştır. Birlik **Tercihleri** iletişim kutusunu kapatın.

    ![Tercihlerde seçilen Visual Studio](media/unity-image22.png)

4. **Mac için Visual Studio'da**açmak için **EnemyAI.cs** çift tıklayın.

    ![Düşman varlığı birlik içinde seçildi](media/unity-image23.png)

5. Visual Studio çözümü basittir. Bir **Varlıklar** klasörü **(Finder**aynı) ve daha önce oluşturulan **EnemyAI.cs** komut dosyası içerir. Daha karmaşık projelerde, hiyerarşi büyük olasılıkla Birlik'te gördüğünüzden farklı görünecektir.

    ![Mac için Visual Studio'da çözüm pedi](media/unity-image24.png)

6. **EnemyAI.cs** editörde açık. İlk komut dosyası yalnızca Başlat ve **Güncelleştir** yöntemleri için saplamalar içerir. **Start**

7. Aşağıdaki kodla ilk düşman kodunu değiştirin.

    ```csharp
    public class EnemyAI : MonoBehaviour
    {
        public float Speed = 50;
        private Transform _playerTransform;
        private Transform _myTransform;

        void Start()
        {
            var player = GameObject.FindGameObjectWithTag("Player");
            if (!player)
            {
                Debug.LogError(
                    "Could not find the main player. Ensure it has the player tag set.");
            }
            else
            {
                _playerTransform = player.transform;
            }
            _myTransform = this.transform;
        }

        void Update()
        {
            var moveAmount = Speed * Time.deltaTime;
            _myTransform.position = Vector3.MoveTowards(_myTransform.position,
                _playerTransform.position, moveAmount);

            if (_myTransform.position == _playerTransform.position)
            {
                _myTransform.position = Vector3.back * 10;
            }
        }
    }
    ```

8. Burada tanımlanan basit düşman davranışına hızlıca bir göz atın. **Başlangıç** yönteminde, oyuncu nesnesine (etiketine göre) ve **dönüşümüne**bir gönderme alıyoruz. Her kare olarak adlandırılan **Güncelleştirme** yönteminde, düşman oyuncu nesnesi doğru hareket edecektir. Anahtar kelimeler ve adlar, Mac için Visual Studio'daki kod tabanını anlamayı kolaylaştırmak için renk kodlaması kullanır.

9. Mac için Visual Studio'daki düşman komut dosyasındaki değişiklikleri **kaydedin.**

## <a name="task-3-debugging-the-unity-project"></a>Görev 3: Birlik projesinin hata ayıklanması

1. **Başlat** yönteminde ilk kod satırında bir kesme noktası ayarlayın. Hedef satırdaki düzenleyici kenar boşluğuna tıklayabilir veya satıra imleci yerleyebilir ve **F9**tuşuna basabilirsiniz.

    ![mac için visual studio'da kesme noktası ayarlaması](media/unity-image25.png)

2. Hata **Hata Ayıklama** başlat düğmesini tıklatın veya **F5 tuşuna**basın. Bu projeyi oluşturacak ve hata ayıklama için Birlik'e bağlayacak.

    ![mac için visual studio'da başlatma düğmesi](media/unity-image26.png)

3. **Unity'ye** dönün ve oyunu başlatmak için **Çalıştır** düğmesine tıklayın.

    ![birlik içinde çalıştır düğmesi](media/unity-image27.png)

4. Kesme noktası isabet olmalı ve şimdi Mac hata ayıklama araçları için Visual Studio kullanabilirsiniz.

    ![mac için görsel stüdyoda breakpoint hit](media/unity-image28.png)

5. **Locals** defterinden, **bir EnemyAI nesnesi** başvurulan **bu** işaretçiyi bulun. Başvuruyu genişletin ve **Speed**gibi ilişkili üyelere göz atabileceğinizi görün.

    ![mac için görsel stüdyoda yerliler hata defteri](media/unity-image29.png)

6. **Kopma** noktasını Başlangıç yönteminden, kenar boşluğuna tıklayarak veya satırı seçerek eklendiği şekilde kaldırın ve **F9**tuşuna basın.

    ![mac için görsel stüdyoda breakpoint hit](media/unity-image30.png)

7. **Parametre** olarak bir etiket kullanarak Player oyun nesnesini bulan ilk kod satırının üzerinden adım atmak için **F10** tuşuna basın.

8. Fare imlecini, ilişkili üyelerini görüntülemek için kod düzenleyicisi penceresindeki **oyuncu** değişkeninin üzerine takın. Alt özellikleri görüntülemek için bindirmeyi bile genişletebilirsiniz.

    ![mac editörü için visual studio pencere hata ayıklama](media/unity-image31.png)

9. Yürütmeye devam etmek için **F5** tuşuna basın veya **Çalıştır** düğmesine basın. Düşman küpün tekrar tekrar oyuncu küpüne yaklaştığını görmek için Birlik'e dönün. Görünür değilse kamerayı ayarlamanız gerekebilir.

    ![sahne birlik içinde oynuyor](media/unity-image32.png)

10. **Mac için Visual Studio'ya** geri dön ve **Güncelleştirme** yönteminin ilk satırında bir kesme noktası ayarlayın. Hemen vurulmalı.

    ![mac için visual studio'da bir kesme noktası ayarlama](media/unity-image33.png)

11. Hızın çok hızlı olduğunu ve uygulamayı yeniden başlatmadan değişikliğin etkisini test etmek istediğimizi varsayalım. Otomatik veya Yerel **ler** **penceresindehız** değişkenini bulun ve **"10"** olarak değiştirin ve **Enter**tuşuna basın. **Locals**

    ![yerel penceredeki değişkenleri ayarlama](media/unity-image34.png)

12. Kesme noktasını kaldırın ve yürütmeye devam etmek için **F5** tuşuna basın.

13. Çalışan uygulamayı görüntülemek için **Birlik'e** dönün. Düşman küpü şu anda orijinal hızın beşte birinde hareket ediyor.

    ![çalışan uygulama ile birlik penceresi](media/unity-image35.png)

14. **Tekrar Oynat** düğmesini tıklatarak Unity uygulamasını durdurun.

    ![birlik uygulamasını durdurma](media/unity-image36.png)

15. Mac **için Visual Studio'ya**geri dön. Hata ayıklama oturumunu **Durdur** düğmesine tıklayarak durdurun.

    ![Mac için Visual Studio'da hata ayıklama oturumunu durdurma](media/unity-image37.png)

## <a name="task-4-exploring-unity-features-in-visual-studio-for-mac"></a>Görev 4: Mac için Visual Studio'da Birlik özelliklerini keşfetmek

1. Mac için Visual Studio, kod düzenleyicisi içindeki Unity belgelerine hızlı erişim sağlar. **İmleci Güncelleme** yöntemi içinde **Vector3** simgesinin üzerine yerleştirin ve **komut + '** tuşuna basın.

    ![mac editörü için visual studio yöntemi seçme](media/unity-image38.png)

2. Yeni bir tarayıcı penceresi **Vector3**için belgelere açılır. Memnun olduğunuzda tarayıcı penceresini kapatın.

    ![tarayıcı penceresi belgelere açılır](media/unity-image39.png)

3. Mac için Visual Studio da hızlı bir şekilde Birlik davranış sınıfları oluşturmak için bazı yardımcıları sağlar. **Solution Explorer'dan** **Varlıklar'ı** sağ tıklatın ve **Yeni MonoBehaviour > ekle'yi**seçin.

    ![yeni tek davranışlı bağlam eylemi](media/unity-image40.png)

4. Yeni oluşturulan **sınıf, Başlat** ve **Güncelleştir** yöntemleri için saplamalar sağlar. **Güncelleştirme** yönteminin kapanış ayraç **sonra, "onmouseup"** yazmaya başlayın. Yazarken, Visual Studio'nun IntelliSense'inin uygulamayı planladığınız yönteme hızla sıfırladığını unutmayın. Sağlanan otomatik tamamlama listesinden seçin. Herhangi bir parametre de dahil olmak üzere, sizin için bir yöntem saplama dolduracaktır.

    ![mac için görsel stüdyoda intellisense](media/unity-image41.png)

5. **OnMouseUp** yönteminin içinde **"taban" yazın.** aramak için kullanılabilir tüm temel yöntemleri görmek için. Ayrıca, IntelliSense uçuşunun sağ üst köşesindeki sayfalama seçeneğini kullanarak her fonksiyonun farklı aşırı yüklerini keşfedebilirsiniz.

    ![mac için görsel stüdyoda aşırı yüklemeleri keşfetmek](media/unity-image42.png)

6. Mac için Visual Studio, yeni gölgeleyicileri kolayca tanımlamanızı da sağlar. **Solution**Explorer'dan, **Varlıklar'ı** sağ tıklatın ve **Yeni Shader > ekle'yi**seçin.

    ![mac için görsel stüdyoda yeni shader eylem](media/unity-image43.png)

7. Shader dosya biçimi, okunmasını ve anlaşılmasını kolaylaştırmak için tam renk ve yazı tipi işlemesini alır.

    ![söz dizimi vurgulaması](media/unity-image44.png)

8. **Birliğe**geri dön. Visual Studio for Mac aynı proje sistemiyle çalıştığından, her iki yerde yapılan değişikliklerin diğeriyle otomatik olarak senkronize edildiğini görürsünüz. Artık görev için her zaman en iyi aracı kullanmak kolaydır.

    ![unity varlık paneli](media/unity-image45.png)

## <a name="summary"></a>Özet

Bu laboratuvarda, Mac için Unity ve Visual Studio ile bir oyun oluşturmaya nasıl başlayıp edindiğinizi öğrendiniz. Birlik [https://unity3d.com/learn](https://unity3d.com/learn) hakkında daha fazla bilgi edinmek için bkz.
