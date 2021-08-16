---
title: Unity ile oyun oluşturmaya başlama
description: Unity ve Mac için Visual Studio'i Mac için Visual Studio
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/09/2020
ms.technology: vs-ide-general
ms.assetid: D07FA43B-9D18-4DFA-8343-CD538FAD84DB
ms.topic: how-to
ms.openlocfilehash: 02cfb49a223d927dd8228bb961f2036fe59c050fe5492c4ee2e0e5538e86e931
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121383037"
---
# <a name="getting-started-building-games-with-unity-in-visual-studio-for-mac"></a>Mac için Visual Studio'de Unity ile oyun Mac için Visual Studio

Unity, C# ile oyun geliştirmeyi sağlayan bir oyun altyapısıdır. Bu kılavuzda, Unity ortamının yanı sıra Mac için Visual Studio ve Unity için Mac için Visual Studio Araçları kullanarak Unity oyunlarını geliştirmeye ve hata ayıklamaya nasıl başlanır?

Mac için Visual Studio Unity araçları, yenileriyle birlikte yüklenmiş ücretsiz bir Mac için Visual Studio. Unity geliştiricilerinin, mükemmel IntelliSense desteği, hata ayıklama özellikleri Mac için Visual Studio ve daha fazlasını içeren Mac için Visual Studio özelliklerinden yararlanmasını sağlar.

## <a name="objectives"></a>Hedefler

> [!div class="checklist"]
> * Mac için Visual Studio ile Unity geliştirme hakkında bilgi Mac için Visual Studio

## <a name="prerequisites"></a>Önkoşullar

- Mac için Visual Studio ( [https://www.visualstudio.com/vs/mac](https://www.visualstudio.com/vs/visual-studio-mac) )
- Unity 5.6.1 Personal Edition veya daha yenisi ( [https://store.unity.com](https://store.unity.com/) , unity.com hesabı gerektirir)

## <a name="intended-audience"></a>Hedef Kitle

Bu laboratuvar, C# hakkında bilgi sahibi olan geliştiricilere yöneliktir ancak derin deneyim gerekli değildir.

## <a name="task-1-creating-a-basic-unity-project"></a>1. Görev: Temel bir Unity projesi oluşturma

1. **Unity'i başlatma.** İstekte bulunduysanız oturum açma.

2. Yeni **'ye tıklayın.**

    ![Unity'de yeni düğme](media/unity-image1.png)

3. İlke **Project** **"UnityLab" olarak ayarlayın ve** **3B'yi seçin.** Proje **oluştur'a tıklayın.**

    ![yeni proje oluşturma ekranı](media/unity-image2.png)

4. Şimdi varsayılan Unity arabirimine bakabilirsiniz. Sol tarafta oyun nesnelerinin bulunduğu sahne hiyerarşisi, ortada gösterilen boş sahnenin 3D görünümü, altta proje dosyaları bölmesi ve sağ tarafta denetçi ve hizmetler bulunur. Elbette bundan çok daha fazlası vardır, ancak bunlar en önemli bileşenlerden birkaçıdır.

    ![boş unity arabirimi](media/unity-image3.png)

5. Unity'de yeni olan geliştiriciler için, uygulamanıza çalışan her şey bir sahne bağlamında **mevcut olacaktır.** Sahne dosyası, geçerli sahne ve özellikleri için projede kullanılan kaynaklar hakkında her türlü meta verileri içeren tek bir dosyadır. Uygulamanızı bir platform için paketleyenin, sonuçta elde edilen uygulama bir veya daha fazla sahnenin bir koleksiyonuna ek olarak, ekley koleksiyonunuz olur. Bir projede istediğiniz kadar sahneniz olabilir.

6. Yeni sahnenin içinde yalnızca bir kamera ve yön ışığı vardır. Sahne, herhangi bir **şeyin** görünür olması için bir kamera ve herhangi bir şeyin **duyulabilir** olması için Ses Dinleyicisi gerektirir. Bu bileşenler bir **GameObject nesnesine ekli.**

7. Hiyerarşi **bölmesinden** Ana Kamera **nesnesini** seçin.

    ![hiyerarşi bölmesinde vurgulanmış ana kamera nesnesi](media/unity-image4.png)

8. Özelliklerini **gözden** geçirmek için pencerenin sağ tarafındaki Denetçi bölmesini seçin. Kamera özellikleri arasında dönüştürme bilgileri, arka plan, projeksiyon türü, görünüm alanı gibi özellikler yer alıyor. Varsayılan olarak, kameraya bağlı bir sanal mikrofondan sahne sesi işen bir Ses Dinleyicisi bileşeni de eklenmiştir.

    ![denetçi bölmesi](media/unity-image5.png)

9. **Directional Light nesnesini** seçin. Bu, gölgelendiriciler gibi bileşenlerin nesneleri nasıl işley bileşenlerinin bilgili olduğunu açık bir şekilde gösterir.

    ![vurgulanmış yön ışığı nesnesi](media/unity-image6.png)

10. Denetçiyi **kullanarak** tür, renk, yoğunluk, gölge tür gibi genel aydınlatma özelliklerini içerir.

    ![denetçi bölmesindeki özelliklere bakma](media/unity-image7.png)

11. Unity'de projelerin diğer projelerden biraz farklı olduğunu Mac için Visual Studio önemlidir. Alttaki **Project** sekmesinde Varlıklar klasörüne sağ tıklayın ve **Bulıcı'da** Ortaya **Çıkar'ı seçin.**

    ![bulıcı bağlam eylemde ortaya çıkar](media/unity-image8.png)

12. Projeler, **gördüğünüz** **gibi Varlıklar,** Kitaplık, **ProjectSettings** ve Geçici klasörleri içerir.  Ancak, arabirimde yalnızca **Assets** klasörü görünür. Kitaplık **klasörü,** içe aktarılan varlıklar için yerel önbellektir; Varlıklar için tüm meta verileri tutar. **ProjectSettings klasörü,** yapılandırabilirsiniz ayarları depolar. Geçici **klasör,** derleme işlemi sırasında Mono ve Unity'den geçici dosyalar için kullanılır. Ayrıca, Mac için Visual Studio **(UnityLab.sln)** içinde açabilirsiniz.

    ![bulıcıda varlıklar](media/unity-image9.png)

13. Bulıcı **penceresini kapatın** ve Unity'ye geri **döner.**

14. **Assets klasörü** tüm assets-art, code, audio vb. dosyalarını içerir. Artık boş, ancak projenize getirdiğiniz her dosya buraya gider. Bu her zaman Unity Düzenleyicisi'nde en üst **düzey klasördür.** Ancak dosyaları her zaman Unity arabirimi (veya Mac için Visual Studio) aracılığıyla ekleyin ve kaldırın ve hiçbir zaman doğrudan dosya sistemi aracılığıyla kaldırmayın.

    ![unity'de assets klasörü](media/unity-image10.png)

15. **GameObject;** modeller, ışıklar, parçacık sistemleri gibi neredeyse her şey bu türden türetilse de Unity'de geliştirmenin merkezidir. 3D **Object** > Cube menüsünde **GameObject > yeni bir Cube nesnesi ekleyin.**

    ![sahnede küp nesnesi](media/unity-image11.png)

16. Yeni **GameObject'in** özelliklerine hızlıca göz atarak ad, etiket, katman ve dönüştürme özelliklerine bakın. Bu özellikler tüm **GameObjects için ortaktır.** Ayrıca, örgü filtresi, kutu **harmanlayıcı** ve işleyici gibi gerekli işlevleri sağlamak için Küp'e birkaç bileşen ekli.

    ![oyun nesnesi özellikleri](media/unity-image12.png)

17. Varsayılan olarak **"Küp"** adına sahip **Olan Küp nesnesini "Tamam"** **olarak yeniden adlandırabilirsiniz.** Değişikliği kaydetmek için **Enter tuşuna** basın. Bu, basit oyunumuza göre küp küpü olacak.

    ![küp nesnesi yeniden adlandırma özelliği](media/unity-image13.png)

18. Yukarıdakiyle aynı işlemi kullanarak sahneye başka bir **Cube** nesnesi ekleyin ve bu nesneyi **"Player" olarak ad girin.**

    ![ikinci küp nesnesini yeniden adlandırma](media/unity-image14.png)

19. Oynatıcı nesnesini **de "Player"** olarak etiketle **(ad** alanı altındaki Etiket açılan denetimine bakın). Bunu oyuncu oyunu nesnesinin bulunmasına yardımcı olmak için betikte kullan kullanırsınız.

    ![oynatıcı nesnesini etiketleme](media/unity-image15.png)

20. Sahne **görünümünde,** fareyi kullanarak oyuncu nesnesini Z ekseninde yer alan nesneden uzaklaştırabilirsiniz. Küpü seçerek ve kırmızı panelden mavi çizgiye sürükleyerek Z **ekseninde** **hareket ettirebilirsiniz.** Küp 3D alanda yaşadığından ancak her zaman yalnızca 2D'ye sürüklenene kadar sürüklendiği eksen özellikle önemlidir.

    ![küpü gösteren sahne görünümü](media/unity-image16.png)

21. Küpü eksen boyunca aşağı ve sağa hareket ettirin. Bu, **Denetçi'de Transform.Position** özelliğini **günceller.** Laboratuvardaki sonraki adımları kolaylaştırmak için burada gösterilene benzer bir konuma sürüklemeyi deneyin.

    ![bir küpü eksen üzerinde taşıma](media/unity-image17.png)

22. Artık mantıksal mantığın oyuncuyu takip etmek için biraz kod eklemesi gerekir. Project penceresinde **Assets** **klasörüne sağ** tıklayın ve **C# Betiği >'yi seçin.**

    ![C# betik bağlamı eylemi](media/unity-image18.png)

23. Yeni C# betiğine **"Arakai" adını girin.**

    ![C# betiği](media/unity-image19.png)

24. Oyun nesnelerine betikler eklemek için, yeni oluşturulan betiği Hiyerarşi **bölmesindeKimlik** **nesnesine** sürükleyin. Artık bu nesne bu betikten davranışları kullanacak.

    ![oyun nesnesine betik eklemeyi gösteren vurgulama](media/unity-image20.png)

25. Geçerli **sahneyi > Için Dosya Ve** Sahneleri Kaydet'i seçin. **"MyScene" olarak ad girin.**

## <a name="task-2-working-with-visual-studio-for-mac-tools-for-unity"></a>Görev 2: Unity için Mac için Visual Studio Araçlarıyla Çalışma

1. C# kodunu düzenlemenin en iyi yolu, Mac için Visual Studio. Unity'yi varsayılan işleyicisi Mac için Visual Studio kullanmak üzere yapılandırarak. Unity **> Tercihler'i seçin.**

2. Dış **Araçlar sekmesini** seçin. Dış **Betik Düzenleyicisi açılan listesinde** Gözat'ı seçin **ve** **Uygulamalar/Visual Studio.app öğesini seçin.** Alternatif olarak, önceden bir Visual Studio **seçeneği** varsa bunu seçmeniz gerekir.

    ![tercihler'de dış araçlar sekmesi](media/unity-image21.png)

3. Unity artık betik düzenlemesi için **Mac için Visual Studio** kullanacak şekilde yapılandırılmıştır. **Unity tercihleri** iletişim kutusunu kapatın.

    ![Visual Studio tercihlerinde seçili](media/unity-image22.png)

4. **Mac için Visual Studio**' de açmak için **enemyai. cs** ' ye çift tıklayın.

    ![Unity 'de seçili rakip varlık](media/unity-image23.png)

5. Visual Studio çözümü basittir. Daha önce oluşturulan bir **varlıklar** klasörünü ( **Finder**'dan aynı bir tane) ve **enemyai. cs** betiğini içerir. Daha karmaşık projelerde hiyerarşi, Unity 'de görenden farklı şekilde görünür.

    ![Mac için Visual Studio çözüm penceresi](media/unity-image24.png)

6. **Enemyai. cs** düzenleyicide açıktır. Başlangıç betiği yalnızca **Start** ve **Update** yöntemleri için saplamalar içerir.

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

8. Burada tanımlanan basit rakip davranışına hızlıca göz atın. **Start** yönteminde, Player nesnesine (etiketine göre) ve **dönüşümünü** de bir başvuruya sunuyoruz. Her çerçeve olarak çağrılan **Update** yönteminde, rakip, oynatıcı nesnesine doğru hareket eder. anahtar sözcükler ve adlar, Mac için Visual Studio kod temelinin anlaşılması daha kolay hale getirmek için renk kodlaması kullanır.

9. **Mac için Visual Studio**, rakip betikteki değişiklikleri kaydedin.

## <a name="task-3-debugging-the-unity-project"></a>Görev 3: Unity projesinde hata ayıklama

1. **Başlangıç** yöntemindeki kodun ilk satırında bir kesme noktası ayarlayın. Hedef satırdaki Düzenleyici kenar boşluğuna tıklayabilir ya da imleci satıra yerleştirebilir ve **F9** tuşuna basabilirsiniz.

    ![Mac için Visual Studio kesme noktası ayarlanıyor](media/unity-image25.png)

2. **Hata ayıklamayı Başlat** düğmesine tıklayın veya **F5**'e basın. Bu, projeyi oluşturacak ve hata ayıklama için Unity 'ye ekleyecek.

    ![Mac için Visual Studio 'de başlat düğmesi](media/unity-image26.png)

3. **Unity** 'ye dönün ve **Çalıştır** düğmesine tıklayarak oyunu başlatın.

    ![Unity 'de Çalıştır düğmesi](media/unity-image27.png)

4. kesme noktası isabet etmelidir ve artık Mac için Visual Studio hata ayıklama araçlarını kullanabilirsiniz.

    ![kesme noktası isabet Mac için Visual Studio](media/unity-image28.png)

5. **Yereller** penceresinde, bir **Enemyai** nesnesine başvuran **Bu** işaretçiyi bulun. Başvuruyu genişletin ve **hız** gibi ilişkili üyelere gözatabileceğiniz hakkında bilgi için bkz..

    ![Mac için Visual Studio 'teki yereller penceresi](media/unity-image29.png)

6. **Başlangıç** yönteminden kesme noktasını, kenar boşluğunda tıklayarak veya satırı seçip **F9** tuşuna basarak kaldırın.

    ![Mac için Visual Studio üzerine tıklayarak bir kesme noktasını kaldırma](media/unity-image30.png)

7. Bir etiketi parametre olarak kullanarak **Player** oyun nesnesini bulan ilk kod satırının üzerine gitmek için **F10** tuşuna basın.

8. İlişkili üyelerini görüntülemek için fare imlecini kod Düzenleyicisi penceresindeki **oyuncu** değişkeninin üzerine getirin. Alt özellikleri görüntülemek için de kaplamayı genişletebilirsiniz.

    ![Mac için Visual Studio düzenleyicisinde hata ayıklama penceresi](media/unity-image31.png)

9. Yürütmeye devam etmek için **F5** tuşuna basın veya **Çalıştır** düğmesine basın. Rakip küpünü Player küpüne sürekli olarak yaklaşımı görmek için Unity 'ye dönün. Kamerayı, görünür değilse ayarlamanız gerekebilir.

    ![Unity 'de sahne oynama](media/unity-image32.png)

10. **Mac için Visual Studio** 'e dönün ve **Update** yönteminin ilk satırında bir kesme noktası ayarlayın. Hemen isabet edilmelidir.

    ![Mac için Visual Studio kesme noktası kaldırılıyor](media/unity-image33.png)

11. Hızının çok hızlı olduğunu ve uygulamanın yeniden başlatılmasına gerek kalmadan değişikliğin etkisini test etmek istiyoruz. **Hızlı** değişkeni, **oto** veya **Yereller** penceresinde bulun ve ardından **"10"** olarak değiştirin ve **ENTER** tuşuna basın.

    ![Yereller penceresindeki değişkenleri ayarlama](media/unity-image34.png)

12. Kesme noktasını kaldırın ve yürütmeyi sürdürmesini sağlamak için **F5** 'e basın.

13. Çalışan uygulamayı görüntülemek için **Unity** 'ye dönün. Rakip küp, artık özgün hızdan beşinci olarak taşınıyor.

    ![çalışan uygulamayla Unity penceresi](media/unity-image35.png)

14. **Oynat** düğmesine tekrar tıklayarak Unity uygulamasını durdurun.

    ![Unity uygulamasını durdurma](media/unity-image36.png)

15. **Mac için Visual Studio** dön. **Durdur** düğmesine tıklayarak hata ayıklama oturumunu durdurun.

    ![Mac için Visual Studio hata ayıklama oturumu durduruluyor](media/unity-image37.png)

## <a name="task-4-exploring-unity-features-in-visual-studio-for-mac"></a>görev 4: Mac için Visual Studio Unity özelliklerini keşfetme

1. Mac için Visual Studio, kod düzenleyicisi içinde Unity belgelerine hızlı erişim sağlar. İmleci **Vector3** simgesine **Update** yönteminde bir yere yerleştirin ve **⌘ Command + '** tuşlarına basın.

    ![Mac için Visual Studio Düzenleyicisi 'nde Yöntem seçme](media/unity-image38.png)

2. **Vector3** belgeleri için yeni bir tarayıcı penceresi açılır. Tatmin edildiğinde tarayıcı penceresini kapatın.

    ![belgeler için tarayıcı penceresi açılır](media/unity-image39.png)

3. Mac için Visual Studio ayrıca, hızlı bir şekilde Unity davranış sınıfları oluşturmak için bazı yardımcılar sağlar. **Çözüm Gezgini**, **varlıklar** ' a sağ tıklayın ve **Yeni > monodavranış Ekle**' yi seçin.

    ![Yeni monodavranış bağlamı eylemi](media/unity-image40.png)

4. Yeni oluşturulan sınıf, **Başlangıç** ve **güncelleştirme** yöntemlerine yönelik saplamalar sağlar. **Güncelleştirme** yönteminin kapanış ayracından sonra **"OnMouseUp"** yazmaya başlayın. siz yazarken, Visual Studio ıntellisense 'in uygulamayı planladığınız yöntemde hızlı bir şekilde sıfırdığına dikkat edin. Bunu, belirtilen otomatik tamamlama listesinden seçin. Herhangi bir parametre dahil, sizin için bir yöntem saplaması dolduracaktır.

    ![Mac için Visual Studio içinde ıntellisense](media/unity-image41.png)

5. **OnMouseUp** yönteminin içinde **"Base** " yazın. çağırmak için kullanılabilir olan tüm temel yöntemleri görmek için. IntelliSense açılır menüsü ' nin sağ üst köşesindeki sayfalama seçeneğini kullanarak her bir işlevin farklı aşırı yüklerini de inceleyebilirsiniz.

    ![Mac için Visual Studio aşırı yüklemeleri keşfetme](media/unity-image42.png)

6. Mac için Visual Studio ayrıca, kolayca yeni gölgelendiriciler tanımlamanızı sağlar. **Çözüm Gezgini**, **varlıklar** ' a sağ tıklayıp **> yeni gölgelendirici Ekle**' yi seçin.

    ![Mac için Visual Studio yeni gölgelendirici eylemi](media/unity-image43.png)

7. Gölgelendirici dosya biçimi, okumayı ve anlamayı kolaylaştırmak için tam renkli ve yazı tipi işleme alır.

    ![söz dizimi vurgulaması](media/unity-image44.png)

8. **Unity**'ye geri dönün. Mac için Visual Studio aynı proje sistemiyle çalıştığından, her iki yerde yapılan değişiklikler otomatik olarak diğer ile eşitlenecek şekilde görürsünüz. Artık görev için en iyi aracı kullanmak kolaydır.

    ![Unity varlık bölmesi](media/unity-image45.png)

## <a name="summary"></a>Özet

bu laboratuvarda, Unity ve Mac için Visual Studio bir oyun oluşturmaya nasıl başladığınızı öğrendiniz. [https://unity3d.com/learn](https://unity3d.com/learn)Unity hakkında daha fazla bilgi için bkz..
