---
title: Unity ile oyun oluşturmaya başlama
description: Unity ve Mac için Visual Studio kullanmaya başlama
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/20/2019
ms.technology: vs-ide-general
ms.assetid: D07FA43B-9D18-4DFA-8343-CD538FAD84DB
ms.topic: how-to
ms.openlocfilehash: da9c8b3470fee406b577b136b6c55d76c9346e44
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85950656"
---
# <a name="getting-started-building-games-with-unity-in-visual-studio-for-mac"></a>Mac için Visual Studio Unity ile Oyunlar oluşturmaya başlama

Unity, C# dilinde oyun geliştirmenize olanak sağlayan bir oyun altyapısıdır. Bu izlenecek yol, Unity 'nin yanı sıra Unity uzantısı için Mac için Visual Studio ve Mac için Visual Studio araçları kullanılarak Unity oyunları geliştirmeye ve bunların hata ayıklamaya nasıl başlaleyeceğinizi gösterir.

Unity için Mac için Visual Studio Araçları, Mac için Visual Studio yüklenen ücretsiz bir uzantıdır. Unity geliştiricilerinin, mükemmel IntelliSense desteği, hata ayıklama özellikleri ve daha fazlasını içeren Mac için Visual Studio üretkenlik özelliklerinden yararlanmasını sağlar.

## <a name="objectives"></a>Hedefler

> [!div class="checklist"]
> * Mac için Visual Studio ile Unity geliştirme hakkında bilgi edinin

## <a name="prerequisites"></a>Ön koşullar

- Mac için Visual Studio ( [https://www.visualstudio.com/vs/mac](https://www.visualstudio.com/vs/visual-studio-mac) )
- Unity 5.6.1 Personal Edition veya üzeri ( [https://store.unity.com](https://store.unity.com/) , çalıştırmak için bir Unity.com hesabı gerekir)

## <a name="intended-audience"></a>Hedef Kitle

Bu laboratuvar, C# hakkında bilgi sahibi olan geliştiricilere yöneliktir, ancak derin deneyim gerekli değildir.

## <a name="task-1-creating-a-basic-unity-project"></a>Görev 1: temel bir Unity projesi oluşturma

1. **Unity**'yi başlatın. İsteniyorsa oturum açın.

2. **Yeni**' ye tıklayın.

    ![Unity 'de yeni düğme](media/unity-image1.png)

3. **Proje adını** **"unitylab"** olarak ayarlayın ve **3B**' i seçin. **Proje oluştur**' a tıklayın.

    ![Yeni Proje ekranı oluştur](media/unity-image2.png)

4. Artık varsayılan Unity arabirimine bakıyorsunuz. Sol taraftaki oyun nesneleriyle sahne alanı, ortadaki boş sahnenin 3B görünümü, altta bulunan bir proje dosyaları bölmesi ve sağdaki Inspector ve hizmetler bulunur. Kuşkusuz, bu kadar çok daha fazla önemli bileşen vardır.

    ![boş Unity arabirimi](media/unity-image3.png)

5. Unity için yeni olan geliştiriciler için, uygulamanızda çalışan her şey bir **sahnenin**bağlamı içinde bulunur. Sahne dosyası, geçerli sahne ve özellikleri için projede kullanılan kaynaklarla ilgili tüm meta veri türlerini içeren tek bir dosyadır. Uygulamanızı bir platform için paketlemeyi yaparken, sonuçta elde edilen uygulama bir veya daha fazla sahnelerin toplanması ve eklediğiniz platforma bağlı herhangi bir kod ile sona acaktır. Bir projede istenen sayıda sahnede sahip olabilirsiniz.

6. Yeni sahneye yalnızca bir kamera ve bir yönlü ışığı vardır. Bir sahne, her şeyin görünür olması için bir **Kamera** ve her şeyin duyulabilir olması Için bir **Ses dinleyicisi** gerektirir. Bu bileşenler bir **Gameobject**'e eklenir.

7. **Hiyerarşi** bölmesinden **ana kamera** nesnesini seçin.

    ![Hiyerarşi bölmesinde vurgulanan ana kamera nesnesi](media/unity-image4.png)

8. Pencerenin sağ tarafındaki **Inspector** bölmesini seçerek özelliklerini gözden geçirin. Kamera Özellikleri, dönüştürme bilgilerini, arka planı, projeksiyon türünü, görünümün alanını vb. içerir. Varsayılan olarak bir ses dinleyicisi bileşeni de eklenmiştir ve bu, temelde, kameraya bağlı bir sanal mikrofondan sahne sesi oluşturur.

    ![Inspector bölmesi](media/unity-image5.png)

9. **Yönlü ışık** nesnesini seçin. Bu, gölgelendiricilerin, nesnelerin nasıl işleneceğini bilmesi için ışık sağlar.

    ![Yön ışığı nesnesi vurgulanmış](media/unity-image6.png)

10. Türü, rengi, yoğunluğu, gölge türü vb. dahil olmak üzere ortak aydınlatma özelliklerini içerdiğini görmek için **Inspector** 'ı kullanın.

    ![Inspector bölmesindeki özelliklere bakma](media/unity-image7.png)

11. Unity 'deki projelerin Mac için Visual Studio karşılıklarından biraz farklı olduğunu göstermek önemlidir. Alttaki **Proje** sekmesinde, **varlıklar** klasörüne sağ tıklayın ve **Finder 'da açığa çıkar**' ı seçin.

    ![Bulucu bağlam eyleminde açığa çıkar](media/unity-image8.png)

12. Projeler, görebileceğiniz gibi **varlıkları**, **kitaplığı**, **ProjectSettings**ve **Temp** klasörlerini içerir. Ancak, arabiriminde görünen tek bir tane **varlıklar** klasörüdür. **Kitaplık** klasörü, içeri aktarılan varlıklar için yerel önbelleğidir; varlıklar için tüm meta verileri barındırır. **ProjectSettings** klasörü yapılandırabileceğiniz ayarları depolar. **Temp** klasörü, derleme Işlemi sırasında Mono ve Unity 'den geçici dosyalar için kullanılır. Ayrıca Mac için Visual Studio (**Unitylab. sln** burada) açabileceğiniz bir çözüm dosyası de vardır.

    ![Finder 'daki varlıklar](media/unity-image9.png)

13. **Bulucu** penceresini kapatın ve **Unity**'ye dönün.

14. **Varlıklar** klasörü, tüm varlıklarınızı (sanat, kod, ses vb.) içerir. Artık boştur, ancak projenize getirdiğiniz her bir dosya buraya gelir. Bu, **Unity düzenleyicisinde**her zaman en üst düzey klasördür. Ancak, dosyaları her zaman Unity arabirimi (veya Mac için Visual Studio) aracılığıyla ve dosya sistemi aracılığıyla doğrudan ekleme ve kaldırma.

    ![Unity 'de varlıklar klasörü](media/unity-image10.png)

15. **Oyun nesnesi** , modeller, ışıklar, parçacık sistemleri gibi bu türden türetilen neredeyse her şey, Unity 'de geliştirme için merkezi bir modeldir. **Gameobject > 3D nesne > küp** menüsünü kullanarak sahneye yeni bir **küp** nesnesi ekleyin.

    ![Sahnedeki küp nesnesi](media/unity-image11.png)

16. Yeni **oyun nesnesinin** özelliklerine hızlıca göz atın ve bir ad, etiket, katman ve dönüşüm olduğunu görün. Bu özellikler tüm **Gameobjects**için ortaktır. Ayrıca, kafes filtresi, Box Collider ve işleyici gibi gerekli işlevleri sağlamak üzere **küpe** birkaç bileşen eklenmiştir.

    ![oyun nesnesi özellikleri](media/unity-image12.png)

17. **"Cube"** adlı **küp** nesnesini, varsayılan olarak **"rakip"** olarak yeniden adlandırın. Değişikliği kaydetmek için **ENTER** tuşuna bastığınızdan emin olun. Bu, basit oyunumuzdaki rakip kübü olacaktır.

    ![küp nesnesi özelliği yeniden adlandır](media/unity-image13.png)

18. Yukarıdaki ile aynı işlemi kullanarak sahneye başka bir **küp** nesnesi ekleyin ve bunu **"oynatıcı"** olarak adlandırın.

    ![ikinci küp nesnesini yeniden adlandır](media/unity-image14.png)

19. Player nesnesi **"oynatıcı"** da etiketleyin (yalnızca ad alanı altında **Tag** açılan kutusu denetimine bakın). Bunu, Player oyun nesnesini bulmaya yardımcı olması için rakip betiğiyle kullanacağız.

    ![oynatıcı nesnesini etiketleme](media/unity-image15.png)

20. **Sahne** görünümünde, fare kullanarak oyuncu nesnesini Z ekseni üzerinde yer alarak rakip nesneden uzağa taşıyın. Küp ' i seçerek ve **mavi** çizgiye doğru **kırmızı** paneline sürükleyerek Z ekseni üzerinde geçiş yapabilirsiniz. Küp 3B alanda bulunduğundan ancak her seferinde yalnızca 2B sürüklenirse, sürüklediğiniz eksen özellikle önemlidir.

    ![kübü gösteren sahne görünümü](media/unity-image16.png)

21. Kübü eksen üzerinde aşağı aşağı doğru aşağı taşıyın. Bu, **Inspector**'daki **Transform. Position** özelliğini güncelleştirir. Daha sonraki adımları laboratuvarda daha kolay hale getirmek için burada görüntülendiklere benzer şekilde bir konuma sürüklediğinizden emin olun.

    ![bir küpü eksen üzerinde taşıma](media/unity-image17.png)

22. Artık rakip mantığını bir miktar kod ekleyerek oynatıcıyı izlemek için bir kod ekleyebilirsiniz. **Proje** panelindeki **varlıklar** klasörüne sağ tıklayın ve **> C# betiği oluştur**' u seçin.

    ![C# betik bağlamı eylemi](media/unity-image18.png)

23. Yeni C# betiğini **"Enemyai"** olarak adlandırın.

    ![C# betiği](media/unity-image19.png)

24. Oyun nesnelerine komut dosyaları eklemek için, yeni oluşturulan betiği **hiyerarşi** bölmesindeki **rakip** nesnesine sürükleyin. Artık bu nesne, bu betikteki davranışları kullanacaktır.

    ![oyun nesnesine betik ekleme gösteren vurgulama](media/unity-image20.png)

25. Geçerli sahneyi kaydetmek için **dosya > sahneleri kaydet** ' i seçin. **"Mysah"** olarak adlandırın.

## <a name="task-2-working-with-visual-studio-for-mac-tools-for-unity"></a>2. görev: Unity için Mac için Visual Studio araçlarıyla çalışma

1. C# kodunu düzenlemenin en iyi yolu Mac için Visual Studio kullanmaktır. Unity 'yi varsayılan işleyicisi olarak Mac için Visual Studio kullanacak şekilde yapılandırabilirsiniz. **Unity > tercihlerini**seçin.

2. **Dış araçlar** sekmesini seçin. **Dış betik Düzenleyicisi** açılan menüsünde, **Araştır** ' ı seçin ve **uygulamalar/Visual Studio. app**' i seçin. Alternatif olarak, zaten bir **Visual Studio** seçeneği varsa, bunu seçmeniz yeterlidir.

    ![Tercihler 'de Dış Araçlar sekmesi](media/unity-image21.png)

3. Unity artık betik düzenlemesi için **Mac için Visual Studio** kullanacak şekilde yapılandırılmıştır. **Unity tercihleri** iletişim kutusunu kapatın.

    ![Tercihlerinde Visual Studio seçildi](media/unity-image22.png)

4. **Mac için Visual Studio**açmak için **EnemyAI.cs** öğesine çift tıklayın.

    ![Unity 'de seçili rakip varlık](media/unity-image23.png)

5. Visual Studio çözümü basittir. Daha önce oluşturulan bir **varlıklar** klasörü ( **Finder**'dan aynı bir tane) ve **EnemyAI.cs** betiği içerir. Daha karmaşık projelerde hiyerarşi, Unity 'de görenden farklı şekilde görünür.

    ![Mac için Visual Studio çözüm paneli](media/unity-image24.png)

6. **EnemyAI.cs** , düzenleyicide açıktır. Başlangıç betiği yalnızca **Start** ve **Update** yöntemleri için saplamalar içerir.

7. İlk rakip kodu aşağıdaki kodla değiştirin.

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

8. Burada tanımlanan basit rakip davranışına hızlıca göz atın. **Start** yönteminde, Player nesnesine (etiketine göre) ve **dönüşümünü**de bir başvuruya sunuyoruz. Her çerçeve olarak çağrılan **Update** yönteminde, rakip, oynatıcı nesnesine doğru hareket eder. Anahtar sözcükler ve adlar, Mac için Visual Studio kod temelinin anlaşılması daha kolay hale getirmek için renk kodlaması kullanır.

9. **Mac için Visual Studio**, rakip betikteki değişiklikleri kaydedin.

## <a name="task-3-debugging-the-unity-project"></a>Görev 3: Unity projesinde hata ayıklama

1. **Başlangıç** yöntemindeki kodun ilk satırında bir kesme noktası ayarlayın. Hedef satırdaki Düzenleyici kenar boşluğuna tıklayabilir ya da imleci satıra yerleştirebilir ve **F9**tuşuna basabilirsiniz.

    ![Mac için Visual Studio 'da kesme noktası ayarlama](media/unity-image25.png)

2. **Hata ayıklamayı Başlat** düğmesine tıklayın veya **F5**'e basın. Bu, projeyi oluşturacak ve hata ayıklama için Unity 'ye ekleyecek.

    ![Mac için Visual Studio 'da Başlat düğmesi](media/unity-image26.png)

3. **Unity** 'ye dönün ve **Çalıştır** düğmesine tıklayarak oyunu başlatın.

    ![Unity 'de Çalıştır düğmesi](media/unity-image27.png)

4. Kesme noktası isabet etmelidir ve artık Mac için Visual Studio hata ayıklama araçlarını kullanabilirsiniz.

    ![Mac için Visual Studio 'da kesme noktası isabeti](media/unity-image28.png)

5. **Yereller** panelinde, bir **Enemyai** nesnesine başvuran **Bu** işaretçiyi bulun. Başvuruyu genişletin ve **hız**gibi ilişkili üyelere gözatabileceğiniz hakkında bilgi için bkz..

    ![Mac için Visual Studio 'da yerel öğeler hata ayıklama paneli](media/unity-image29.png)

6. **Başlangıç** yönteminden kesme noktasını, kenar boşluğunda tıklayarak veya satırı seçip **F9**tuşuna basarak kaldırın.

    ![Mac için Visual Studio 'da kesme noktası isabeti](media/unity-image30.png)

7. Bir etiketi parametre olarak kullanarak **Player** oyun nesnesini bulan ilk kod satırının üzerine gitmek için **F10** tuşuna basın.

8. İlişkili üyelerini görüntülemek için fare imlecini kod Düzenleyicisi penceresindeki **oyuncu** değişkeninin üzerine getirin. Alt özellikleri görüntülemek için de kaplamayı genişletebilirsiniz.

    ![Mac için Visual Studio Düzenleyicisi 'nde hata ayıklama penceresi](media/unity-image31.png)

9. Yürütmeye devam etmek için **F5** tuşuna basın veya **Çalıştır** düğmesine basın. Rakip küpünü Player küpüne sürekli olarak yaklaşımı görmek için Unity 'ye dönün. Kamerayı, görünür değilse ayarlamanız gerekebilir.

    ![Unity 'de sahne oynama](media/unity-image32.png)

10. **Mac için Visual Studio** 'e dönün ve **Update** yönteminin ilk satırında bir kesme noktası ayarlayın. Hemen isabet edilmelidir.

    ![Mac için Visual Studio 'da bir kesme noktası ayarlama](media/unity-image33.png)

11. Hızının çok hızlı olduğunu ve uygulamanın yeniden başlatılmasına gerek kalmadan değişikliğin etkisini test etmek istiyoruz. **Hızlı** değişkeni, **oto** veya **Yereller** penceresinde bulun ve ardından **"10"** olarak değiştirin ve **ENTER**tuşuna basın.

    ![Yereller penceresindeki değişkenleri ayarlama](media/unity-image34.png)

12. Kesme noktasını kaldırın ve yürütmeyi sürdürmesini sağlamak için **F5** 'e basın.

13. Çalışan uygulamayı görüntülemek için **Unity** 'ye dönün. Rakip küp, artık özgün hızdan beşinci olarak taşınıyor.

    ![çalışan uygulamayla Unity penceresi](media/unity-image35.png)

14. **Oynat** düğmesine tekrar tıklayarak Unity uygulamasını durdurun.

    ![Unity uygulamasını durdurma](media/unity-image36.png)

15. **Mac için Visual Studio**dön. **Durdur** düğmesine tıklayarak hata ayıklama oturumunu durdurun.

    ![Mac için Visual Studio hata ayıklama oturumu durduruluyor](media/unity-image37.png)

## <a name="task-4-exploring-unity-features-in-visual-studio-for-mac"></a>Görev 4: Mac için Visual Studio Unity özelliklerini keşfetme

1. Mac için Visual Studio, kod Düzenleyicisi içinde Unity belgelerine hızlı erişim sağlar. İmleci **Vector3** simgesine **Update** yönteminde bir yere yerleştirin ve **⌘ Command + '** tuşlarına basın.

    ![Mac için Visual Studio Düzenleyicisi 'nde Yöntem seçme](media/unity-image38.png)

2. **Vector3**belgeleri için yeni bir tarayıcı penceresi açılır. Tatmin edildiğinde tarayıcı penceresini kapatın.

    ![belgeler için tarayıcı penceresi açılır](media/unity-image39.png)

3. Mac için Visual Studio Ayrıca, hızlı bir şekilde Unity davranış sınıfları oluşturmak için bazı yardımcılar sağlar. **Çözüm Gezgini**, **varlıklar** ' a sağ tıklayın ve **Yeni > monodavranış Ekle**' yi seçin.

    ![Yeni monodavranış bağlamı eylemi](media/unity-image40.png)

4. Yeni oluşturulan sınıf, **Başlangıç** ve **güncelleştirme** yöntemlerine yönelik saplamalar sağlar. **Güncelleştirme** yönteminin kapanış ayracından sonra **"OnMouseUp"** yazmaya başlayın. Siz yazarken, Visual Studio 'nun IntelliSense 'in uygulamayı planladığınız yöntemde hızlı bir şekilde sıfırlıdığına dikkat edin. Bunu, belirtilen otomatik tamamlama listesinden seçin. Herhangi bir parametre dahil, sizin için bir yöntem saplaması dolduracaktır.

    ![Mac için Visual Studio 'da IntelliSense](media/unity-image41.png)

5. **OnMouseUp** yönteminin içinde **"Base** " yazın. çağırmak için kullanılabilir olan tüm temel yöntemleri görmek için. IntelliSense açılır menüsü ' nin sağ üst köşesindeki sayfalama seçeneğini kullanarak her bir işlevin farklı aşırı yüklerini de inceleyebilirsiniz.

    ![Mac için Visual Studio 'da aşırı yüklemeleri keşfetme](media/unity-image42.png)

6. Mac için Visual Studio Ayrıca, kolayca yeni gölgelendiriciler tanımlamanızı sağlar. **Çözüm Gezgini**, **varlıklar** ' a sağ tıklayıp **> yeni gölgelendirici Ekle**' yi seçin.

    ![Mac için Visual Studio 'da yeni gölgelendirici eylemi](media/unity-image43.png)

7. Gölgelendirici dosya biçimi, okumayı ve anlamayı kolaylaştırmak için tam renkli ve yazı tipi işleme alır.

    ![söz dizimi vurgulaması](media/unity-image44.png)

8. **Unity**'ye geri dönün. Mac için Visual Studio aynı proje sistemiyle çalıştığından, her iki yerde yapılan değişiklikler otomatik olarak diğer ile eşitlenecek şekilde görürsünüz. Artık görev için en iyi aracı kullanmak kolaydır.

    ![Unity varlık bölmesi](media/unity-image45.png)

## <a name="summary"></a>Özet

Bu laboratuvarda, Unity ve Mac için Visual Studio bir oyun oluşturmaya nasıl başladığınızı öğrendiniz. [https://unity3d.com/learn](https://unity3d.com/learn)Unity hakkında daha fazla bilgi için bkz..
