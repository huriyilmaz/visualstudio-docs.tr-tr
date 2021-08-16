---
title: 'adım adım kılavuz: Gerçekçi bir 3D Spor Top Oluşturma'
description: Gölgelendirici tekniklerini doku kaynaklarıyla birleştirerek gölgelendirici Tasarımcısı ve Görüntü Düzenleyicisi'ni kullanarak Visual Studio topu nasıl oluşturabilirsiniz?
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: af8eb0f3-bf6a-4d1c-ab47-dcd88ab04efa
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-designers
ms.workload:
- multiple
ms.openlocfilehash: 556684893a3e909b2fc252bffc702bfc2de39a3608f811db6df98a413814ca9c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121239772"
---
# <a name="walkthrough-create-a-realistic-3d-billiard-ball"></a>İzlenecek yol: Gerçekçi bir 3B bilardo topu oluşturma

Bu kılavuzda, gölgelendirici Tasarımcısı ve Görüntü Düzenleyicisi'ni kullanarak gerçek bir 3D güneş topu oluşturma Visual Studio. Çeşitli gölgelendirici teknikleri uygun doku kaynaklarıyla birleştirerek, oyun toplarının 3B görünümü elde edilir.

## <a name="prerequisites"></a>Önkoşullar

Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ve becerilere ihtiyacınız vardır:

- Haziran 2010 DirectX SDK'sine dahil edilen DirectX Doku Aracı gibi dokuları bir küp haritasına birleştirmeye yönelik bir araç.

- Visual Studio'da Görüntü Düzenleyicisi hakkında Visual Studio.

- Visual Studio'da Gölgelendirici Tasarımcısı hakkında Visual Studio.

## <a name="create-the-basic-appearance-with-shape-and-texture"></a>Şekil ve doku ile temel görünümü oluşturma

Bilgisayar grafiklerde görünümün en temel öğeleri şekil ve renktir. Bilgisayar benzetimsinde, gerçek dünya nesnesinin şeklini temsil etmek için 3D model kullanmak yaygındır. Daha sonra renk ayrıntısı, doku haritası kullanılarak modelin yüzeyine uygulanır.

Genellikle, bir ressamdan kullanabileceğiniz bir 3D model oluşturması gerekir, ancak bir topun ortak bir şekil (bir küre) olması nedeniyle Gölgelendirici Tasarımcısı'nın zaten yerleşik olarak uygun bir modeli vardır.

Sphere, Gölgelendirici Tasarımcısı'nda varsayılan önizleme şeklidir; Şu anda gölgelendiricinizin önizlemesini görmek için farklı bir şekil kullanıyorsanız, küreye geri dön.

### <a name="to-preview-the-shader-by-using-a-sphere"></a>Bir küre kullanarak gölgelendiricinin önizlemesini görmek için

- Gölgelendirici Tasarımcısı araç çubuğunda Sphere ile **önizleme'yi seçin.**

Sonraki adımda modele doku uygulanan bir gölgelendirici programı oluşturacağız ancak önce kullanabileceğiniz bir doku oluşturmanız gerekir. Bu kılavuzda, Visual Studio'nin bir parçası olan Görüntü Düzenleyicisi'ni kullanarak doku oluşturma adımlarını gösterir, ancak dokuyu uygun bir biçimde kaydeden herhangi bir görüntü düzenleyicisini kullanabilirsiniz.

Özellikler penceresinin **ve Araç** Kutusunun **görüntülendiğinden** emin olun.

### <a name="to-create-a-billiard-ball-texture-by-using-the-image-editor"></a>Görüntü Düzenleyicisi'ni kullanarak bir yumuşak top dokusu oluşturmak için

1. Çalışmak için bir doku oluşturun. Projenize doku ekleme hakkında bilgi için Görüntü Düzenleyicisi'nde Başlarken bölümüne [bakın.](../designers/image-editor.md)

2. Görüntü boyutunu genişliği iki kat yüksek olacak şekilde ayarlayın; Bu, bir dokuyu topun küresel yüzeyine eşlenmiş olduğu için gereklidir. Görüntüyü yeniden boyutlandırmak için Özellikler **penceresinde** Genişlik ve Yükseklik özellikleri için **yeni** **değerler** belirtin. Örneğin, genişliği 512 ve yüksekliği 256 olarak ayarlayın.

3. Bir dokuyu bir küreye nasıl eşlen olduğunu göz bulundurarak, oyun topu için bir doku çizin.

    Doku şuna benzer şekilde görünüyor olmalı:

    ![Topun dokusu](../designers/media/gfx_shader_demo_billiard_art_ball_texture.png)

4. İsteğe bağlı olarak, bu doku için depolama gereksinimlerini azaltmak istiyor olabilir. Bunu yapmak için doku genişliğini yüksekliğiyle eş olacak şekilde azaltarak silebilirsiniz. Bu, dokuyu genişliği boyunca sıkıştırır, ancak doku, küreye eşlenmiş olması nedeniyle, topun işlenmiş olduğu zaman genişletilir. Yeniden boyutlandırma sonrasında doku şuna benzer şekilde görünüyor:

    ![Kareye sıkıştırılmış dokuyu sıkıştırma](../designers/media/gfx_shader_demo_billiard_art_ball_texture_square.png)

   Şimdi bu dokuyu modele uygulanan bir gölgelendirici oluşturabilirsiniz.

### <a name="to-create-a-basic-texture-shader"></a>Temel doku gölgelendiricisi oluşturmak için

1. Birlikte çalışacak bir DGSL gölgelendiricisi oluşturun. Projenize DGSL gölgelendiricisi ekleme hakkında bilgi için Gölgelendirici Tasarımcısı'Başlarken bölümüne [bakın.](../designers/shader-designer.md)

    Varsayılan olarak gölgelendirici grafiği aşağıdaki gibi görünür:

    ![Varsayılan gölgelendirici grafiği](../designers/media/gfx_shader_demo_billiard_step_0.png)

2. Doku örneğinin değerini geçerli piksele uygulaması için varsayılan gölgelendiriciyi değiştirme. Gölgelendirici grafiği aşağıdaki gibi görünür:

    ![Nesneye doku uygulanan gölgelendirici grafı](../designers/media/gfx_shader_demo_billiard_step_1.png)

3. Doku özelliklerini yapılandırarak önceki yordamda oluşturduğunuz dokuyu uygulama. Doku Örneği düğümünün **Texture**  özelliğinin değerini **Texture1** olarak ayarlayın ve ardından aynı özellik penceresinde texture1 özellik grubunun **Filename** özelliğini kullanarak doku dosyasını belirtin. 

   Gölgelendiricinize doku uygulama hakkında daha fazla bilgi için bkz. Nasıl yapılır: Temel doku [gölgelendiricisi oluşturma.](../designers/how-to-create-a-basic-texture-shader.md)

   Artık topun şuna benzer olması gerekir:

   ![Doku topa yakın bir şekilde](../designers/media/gfx_shader_demo_.png)

## <a name="create-depth-with-the-lambert-lighting-model"></a>Lambert aydınlatma modeliyle derinlik oluşturma

Şimdiye kadar kolayca tanınabilir bir at topu oluşturdunız. Ancak düz ve ilginci olmayan bir şekilde görünür. Daha çok, ikna edici bir çoğaltmadan çok bir atlı top resmi gibi görünür. Düz görünüm, basit gölgelendiriciden elde eder ve bu da topun yüzeyindeki her pikselin aynı miktarda ışığı alır gibi davranmasıdır.

Gerçek dünyada ışık, doğrudan bir ışık kaynağıyla yüz yüze olan yüzeylerde en parlak görünür ve ışık kaynağına belirsiz bir açıda olan yüzeylerde daha az parlak görünür. Bunun nedeni, yüzey doğrudan ışık kaynağıyla yüzıldığında ışık ışığının enerjinin en küçük yüzey alanına dağıtılmasıdır. Yüzey ışık kaynağından uzaklaşıyorsa, aynı enerji miktarı giderek daha büyük bir yüzey alanına dağıtılır. Bir ışık kaynağından uzakta yüzleri olan bir yüzey hiç ışık enerjisi alamadan tamamen koyu bir görünüm elde eder. Bir nesnenin yüzeyindeki parlaklığa sahip olan bu varyans, bir nesnenin şeklinin belirt 300 abdlik olduğunu gösteren önemli bir görsel ipucu oluşturur. bu olmadan nesne düz görünür.

Bilgisayar grafiklerinde, *gerçek* dünya aydınlatması görünümünü çoğaltmak için karmaşık, gerçek dünya aydınlatma etkileşimlerinin basitleştirilmiş yaklaşıkları olan aydınlatma modelleri kullanılır. Lambert aydınlatma modeli, önceki paragrafta açıklandığı gibi bir nesnenin yüzeyine yansıyan ışığın miktarını değişkenlik gösterir. Lambert aydınlatma modelini gölgelendiricinize ek olarak topun daha iyi bir 3D görünümüne sahip olduğunu gösterirsiniz.

### <a name="to-add-lambert-lighting-to-your-shader"></a>Gölgelendiricinize Lambert aydınlatması eklemek için

- Lambert aydınlatma değeriyle doku örneğinin değerini değiştirmek için gölgelendiricinizi değiştirme. Gölgelendirici grafın aşağıdaki gibi olması gerekir:

   ![Lambert aydınlatması eklenmiş gölgelendirici grafiği](../designers/media/gfx_shader_demo_billiard_step_2.png)

- İsteğe bağlı olarak gölgelendirici grafiğinin **MaterialDiffuse** özelliğini yapılandırarak aydınlatmanın nasıl davranacağını ayarlayabilirsiniz. Gölgelendirici grafiğinin özelliklerine erişmek için tasarım yüzeyinin boş bir alanı seçin ve ardından Özellikler penceresinde erişmek istediğiniz **özelliği** bulun.

Gölgelendiricinize Lambert aydınlatması uygulama hakkında daha fazla bilgi için bkz. Nasıl [yapılır: Temel Lambert gölgelendiricisi oluşturma.](../designers/how-to-create-a-basic-lambert-shader.md)

Lambert aydınlatması uygulandığında, topun şuna benzer olması gerekir:

![Doyma ve ışıklı masa toplarının yakın yakınlıkları](../designers/media/gfx_shader_demo_billiard_ball_2.png)

## <a name="enhance-the-basic-appearance-with-specular-highlights"></a>Speculer vurgularla temel görünümü geliştirme

Lambert aydınlatma modeli, yalnızca doku gölgelendiricisinde olmayan şekil ve boyut anlayışını sağlar. Öte yandan top topu hala biraz daha güzel bir görünüme sahiptir.

Gerçek bir topun genellikle üzerine düşen ışığın bir kısmını yansıtan bir sözlük bitişi vardır. Bu yansıyan ışığın bazıları, yüzeyin yansıtıcı özelliklerinin benzetimini yapılan speculer vurgularla sonuçlanır. Bitişin özelliklerine bağlı olarak vurgular yerelleştirilmiş veya geniş, yoğun veya ince olabilir. Bu specular yansımalar bir ışık kaynağı, yüzeyin yönü ve kamera konumu arasındaki ilişki kullanılarak modellendi. Diğer bir ifadeyle vurgu, yüzeyin yönü ışık kaynağını doğrudan kameraya yansıtıyorsa vurgu en yoğundur ve yansıma daha az doğrudan olduğunda daha az yoğundur.

Piser aydınlatma modeli, lambert aydınlatma modelini, önceki paragrafta açıklandığı gibi specular vurgular içerecek şekilde inşa edilir. Piser aydınlatma modelini gölgelendiricinize ek olarak, daha ilgi çekici bir görünüm elde etmek için topun simülasyonunu bitirin.

### <a name="to-add-specular-highlights-to-your-shader"></a>Gölgelendiricinize specular vurgular eklemek için

1. Ek karıştırma kullanarak gölgelendiricinizi specular katkıyı içerecek şekilde değiştirme. Gölgelendirici grafın aşağıdaki gibi olması gerekir:

    ![Özel aydınlatma eklenmiş gölgelendirici grafiği](../designers/media/gfx_shader_demo_billiard_step_3.png)

2. İsteğe bağlı olarak, gölgelendirici grafiğinin specular özelliklerini (**MaterialSpecular** ve **MaterialSpecularPower**) yapılandırarak, specular vurgulamanın davranışlarını ayarlayabilirsiniz. Gölgelendirici grafiğinin özelliklerine erişmek için tasarım yüzeyinin boş bir alanı seçin ve özellikler **penceresinde** erişmek istediğiniz özelliği bulun.

   Gölgelendiricinize specular vurgulamaları uygulama hakkında daha fazla bilgi için [bkz. Nasıl yapılır: Temel P shader oluşturma.](../designers/how-to-create-a-basic-phong-shader.md)

   Speculer vurgulama uygulandığında, topun şuna benzer olması gerekir:

   ![Specular eklenmiş olarak at top yakını](../designers/media/gfx_shader_demo_billiard_ball_3.png)

## <a name="create-a-sense-of-space-by-reflecting-the-environment"></a>Ortamı yansıtarak alan algısı oluşturma

Specular vurgular uygulandığında, topun oldukça ikna edici görünüyor. Doğru şekle, doğru boyaya ve doğru bitişe sahip. Öte yandan yine de topun ortamının bir parçası gibi bir görünüme sahip olacak bir teknik daha vardır.

Gerçek bir oyun topuna yakından bakarsanız, bunun sözlük yüzeyinin yalnızca speculer vurgular sergileyemese de çevresindeki dünyanın bir görüntüsünü de yansıtdığını fark edersiniz. Ortamın bir görüntüsünü doku olarak kullanarak ve modelin kendi dokusuyla birleştirerek her pikselin son rengini belirleyerek bu yansımanın benzetimini sebilirsiniz. Ne tür bir bitiş istediğinize bağlı olarak, yansıma dokusunda daha fazla veya daha azı ile gölgelendiricinin geri kalanını birleştirin. Örneğin, yansıtma gibi yüksek oranda yansıtıcı bir yüzeyin benzetimini yapılan gölgelendirici yalnızca yansıma dokusunu kullanabilir, ancak bir gölgelendirici topunda bulunan gibi daha hafif bir yansımayı simüle etmek, yansıma dokusu değerinin yalnızca küçük bir kısmını gölgelendirici hesaplamanın geri kalanıyla bir araya toplar.

Elbette, modelin doku haritasını uygulamakla aynı şekilde modele yansıtilen görüntüyü uygulayanın bir yolu değildir. Böyle bir şey yaptıysanız, dünyanın yansımaları, yansıma ona yapıştırılmış gibi hareket eder. Yansıma herhangi bir yönden geleyeli, herhangi bir açı için yansıma haritası değeri sağlamanın bir yolunu ve yansıma haritasını dünyaya göre yönlendiren bir yol gerekir. Bu gereksinimleri karşılamak için küpün kenarlarını oluşturmak üzere düzenlenmiş altı doku sağlayan, küp haritası adı verilen özel bir doku eşlemesi kullanabilirsiniz. Bu küpün içinden herhangi bir yöne işaret ediyor ve bir doku değeri bulabilirsiniz. Küpün her tarafındaki dokular ortamın görüntülerini içeriyorsa, küpün yüzeyinde doğru konumu örneklemek için herhangi bir yansımanın benzetimini sebilirsiniz. Küpü dünyayla uyumlu tutarak ortamın doğru bir yansımasını elde edersiniz. Küpün örneklemenin nerede olacağını belirlemek için kamera vektörün nesnenin yüzeyinden yansımasını hesaplamalı ve ardından 3B doku koordinatları olarak kullanabilirsiniz. Küp eşlemelerini bu şekilde kullanmak, ortam eşlemesi olarak bilinen yaygın bir *tekniktir.*

Ortam eşlemesi, önceki paragraflarda açıklandığı gibi gerçek yansımaların verimli bir yaklaşık olarak tahmin edilir. Ortamla eşlenmiş yansımaları gölgelendiricinize karıştırarak siyah topun benzetimi yapılan bir sondur ve bu da topun sahnenin daha topraklanmış gibi görünmesini sağlar.

İlk adım bir küp eşleme dokusu oluşturmaktır. Birçok uygulama türünde, özellikle yansıma hafif olduğunda veya ekranda belirgin bir alan kaplarken küp haritasının içeriğinin etkili olması için mükemmel olması gerek değildir. Örneğin, birçok oyun ortam eşlemesi için önceden hesaplanan küp eşlemeleri kullanır ve yansımanın doğru olmadığını gösterir ancak yalnızca her yansıtıcı nesneye en yakın olanı kullanır. Kaba bir tahmin bile genellikle ikna edici bir etki için yeterince iyidir.

### <a name="to-create-textures-for-an-environment-map-by-using-the-image-editor"></a>Görüntü Düzenleyicisi'ni kullanarak ortam haritası için dokular oluşturmak için

1. Çalışmak için bir doku oluşturun. Projenize doku ekleme hakkında bilgi için Görüntü Düzenleyicisi'nde Başlarken bölümüne [bakın.](../designers/image-editor.md)

2. Görüntü boyutunu, genişliğinin yüksekliğine eşit ve iki boyutlu bir güç olacak şekilde ayarlayın; Bu, bir küp eşlemesi dizinleme şeklinden dolayı gereklidir. Görüntüyü yeniden boyutlandırmak için Özellikler **penceresinde** Genişlik ve Yükseklik özellikleri için **yeni** **değerler** belirtin. Örneğin Genişlik ve Yükseklik özelliklerinin  **değerini** 256 olarak ayarlayın.

3. Dokuyu doldurmak için düz bir renk kullanın. Bu doku, küp haritasının alt kısmında yer alır ve bu, tablodaki tablo yüzeyine karşılık gelecektir. Bir sonraki doku için kullanılan rengi unutmayın.

4. Birinciyle aynı boyutta ikinci bir doku oluşturun. Bu doku küp haritasının dört tarafında yinelenir. Bu, bir tablodaki yüzey ve kenarlara ve sonra da tablo çevresindeki alana karşılık gelecektir. Alt dokudakiyle aynı rengi kullanarak bu dokudaki tabloyu çizin. Doku şuna benzer şekilde görünüyor olmalı:

    ![Küp haritasının kenarları için doku](../designers/media/gfx_shader_demo_billiard_art_env_texture_side.png)

    Yansıma haritasının etkili olması için fotoğraf gerçekcül olması gerek olmadığını unutmayın; Örneğin, bu makaledeki görüntüleri oluşturmak için kullanılan küp haritası altı yerine yalnızca dört tane kullanılmıştır.

5. Diğer dokuyla aynı boyutta üçüncü bir doku oluşturun. Bu doku, küp haritasının üst kısmında yer alır ve bu da tablodaki tavana karşılık gelecektir. Yansımanın bu kısmını daha ilginç hale getirirken, önceki yordamda gölgelendiriciye ekleyştirilen specular vurguları pekiştiren bir ek yük ışığı çizin. Doku şuna benzer şekilde görünüyor olmalı:

    ![Küp haritasının en üstünde yer alan doku](../designers/media/gfx_shader_demo_billiard_art_env_texture_top2.png)

   Artık küp haritasının kenarları için tek tek dokular oluşturduğunuza göre, bunları tek *bir .dds* dokusunda depolanmış bir küp haritasında bir araya yapmak için bir araç kullanabilirsiniz. Küp haritasını .dds doku biçiminde kaydedeb olduğu sürece, küp eşlemesi oluşturmak istediğiniz herhangi bir programı kullanabilirsiniz. Bu kılavuz, Haziran 2010 DirectX SDK'sı kapsamındaki DirectX Doku Aracı'nı kullanarak doku oluşturma adımlarını açıklar.

### <a name="to-assemble-a-cube-map-by-using-the-directx-texture-tool"></a>DirectX Doku Aracı'nı kullanarak küp eşlemesi oluşturmak için

1. DirectX Doku Aracı'nın ana menüsünde Dosya Yeni **Doku'ya**  >  **tıklayın.** Yeni **Doku iletişim** kutusu görüntülenir.

2. Doku Türü **grubunda Küp** Haritası **Doku'su seçin.**

3. Boyutlar **grubunda Genişlik** ve Yükseklik için doğru değeri **girin ve** **tamam'ı** **seçin.** Yeni bir doku belgesi görüntülenir. Varsayılan olarak, ilk olarak doku belgesinde gösterilen doku Pozitif X küp **yüzüne** karşılık gelecektir.

4. Doku küpün tarafı için oluşturduğunuz dokuyu küp yüzüne yükleme. Ana menüde Dosya Bu **Küp** Haritası Yüzü üzerinde Aç'ı seçin, küpün tarafı için oluşturduğunuz dokuyu seçin ve ardından  >   **Aç'ı seçin.**

5. Negatif **X,** Pozitif Z ve Negatif Z küp **yüzleri** için 4. adımı yineler.  Bunu yapmak için, yüklemek istediğiniz yüzü görüntülemelisiniz. Farklı bir küp eşlemesi yüzü görüntülemek için ana menüde Küp **EşlemeSi** Yüzü Görüntüle'yi ve ardından görüntülemek  >  istediğiniz yüzü seçin.

6. Pozitif **Y küpü** yüzü için doku küpün üst kısmında oluşturduğunuz dokuyu yükleme.

7. Negatif **Y küpü** yüzü için doku küpün alt kısmında oluşturduğunuz dokuyu yükleme.

8. Dokuyu kaydedin.

   Küp haritasının düzenini şöyle düşünebilirsiniz:

   ![Ortam küp eşlemesi düzeni](../designers/media/gfx_shader_demo_billiard_art_env_texture_top.png)

   En üstte pozitif Y (+Y) küp yüzü yer alan görüntü; ortadaki soldan sağa doğru -X, +Z, +X ve -Z küp yüzleri; en altta -Y küpü yüzü yer aldı.

   Artık gölgelendiriciyi, küp eşleme örneğini gölgelendiricinin geri kalanına karıştıracak şekilde değiştirebilirsiniz.

### <a name="to-add-environment-mapping-to-your-shader"></a>Gölgelendiricinize ortam eşlemesi eklemek için

1. Ek karıştırma kullanarak ortam eşleme katkısını dahil etmek için gölgelendiricinizi değiştirme. Gölgelendirici grafın aşağıdaki gibi olması gerekir:

    ![Her iki yansıtıcı gölgelendirici düğümü türüne yakınlık](../designers/media/gfx_shader_demo_billiard_step_4b.png)

    Gölgelendirici grafı **basitleştirmek için** Çarpın-Ekle düğümünü kullanabileceğinizi unutmayın.

    Ortam eşlemesi uygulayan gölgelendirici düğümlerinin daha ayrıntılı bir görünümü şu şekildedir:

    ![Ortam eşlemesi eklenmiş gölgelendirici grafiği](../designers/media/gfx_shader_demo_billiard_step_4a.png)

2. Küp eşlemesi doku özelliklerini yapılandırarak önceki yordamda oluşturduğunuz dokuyu uygulama. Cubemap Sample düğümünün **Texture** **özelliğinin** değerini Texture2 olarak ayarlayın ve ardından **Texture2** özellik grubunun **Filename** özelliğini kullanarak **doku** dosyasını belirtin.

3. İsteğe bağlı olarak, Sabit düğümün **Output** özelliğini yapılandırarak spor topun yansıtmasını **ayarlayabilirsiniz.** Düğümün özelliklerine erişmek için düğümü seçin ve özellikler **penceresinde** erişmek istediğiniz özelliği bulun.

   Ortam eşlemesi uygulandığında, topun şuna benzer olması gerekir:

   ![Ortamın yakından eşlenen topu](../designers/media/gfx_shader_demo_billiard_ball_4.png)

   Bu son görüntüde, çok ikna edici bir top oluşturmak için eklenen etkilerin nasıl bir araya geldi? Şekil, doku ve aydınlatma, 3B nesnenin temel görünümünü oluşturur ve specular vurgular ve yansımalar, topu daha ilginç hale ve ortamının bir parçası gibi gösterir.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl: Gölgelendiriciyi dışarı aktarma](../designers/how-to-export-a-shader.md)
- [Nasıl yapılır. 3B modele gölgelendirici uygulama](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Gölgelendirici Tasarımcısı](../designers/shader-designer.md)
- [Görüntü Düzenleyicisi](../designers/image-editor.md)
- [Gölgelendirici Tasarımcısı düğümleri](../designers/shader-designer-nodes.md)
