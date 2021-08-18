---
title: 'adım adım kılavuz: Gerçekçi bir 3D Spor Top Oluşturma'
description: Gölgelendirici tekniklerini doku kaynaklarıyla birleştirerek gölgelendirici Tasarımcısı'Visual Studio Görüntü Düzenleyicisi'ni kullanarak 3B gözlük topu oluşturma hakkında bilgi.
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
ms.openlocfilehash: 8c84eb7551f60e67fc49f19b946a56cb39905892
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122051462"
---
# <a name="walkthrough-create-a-realistic-3d-billiard-ball"></a>İzlenecek yol: Gerçekçi bir 3B bilardo topu oluşturma

Bu kılavuzda, gölgelendirici Tasarımcısı ve Görüntü Düzenleyicisi'ni kullanarak gerçek bir 3D güneş topu oluşturma Visual Studio. Çeşitli gölgelendirici teknikleri uygun doku kaynaklarıyla birleştirerek, oyun toplarının 3B görünümü elde edilir.

## <a name="prerequisites"></a>Önkoşullar

Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ve becerilere ihtiyacınız vardır:

- Haziran 2010 DirectX SDK'sine dahil edilen DirectX Doku Aracı gibi dokuları bir küp haritasına birleştirmeye yönelik bir araç.

- Visual Studio'da Görüntü Düzenleyicisi hakkında Visual Studio.

- Visual Studio'de Gölgelendirici Tasarımcısı hakkında Visual Studio.

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

Gerçek bir oyun topuna yakından bakarsanız, bunun sözlük yüzeyinin yalnızca speculer vurgular sergileyemese de çevresindeki dünyanın bir görüntüsünü de yansıtdığını fark edersiniz. Ortamın bir görüntüsünü doku olarak kullanarak ve modelin kendi dokusuyla birleştirerek her pikselin son rengini belirleyerek bu yansımanın benzetimini sebilirsiniz. Ne tür bir bitiş istediğinize bağlı olarak, yansıma dokusunda daha fazla veya daha azı ile gölgelendiricinin geri kalanını birleştirin. Örneğin, yansıtma gibi yüksek oranda yansıtıcı bir yüzeyin benzetimini yapmak için yalnızca yansıma dokusunu kullanabilirsiniz, ancak bir gölgelendirici topunda bulunan gibi daha hafif bir yansımayı simüle etmek için gölgelendirici, yansıma dokusu değerinin yalnızca küçük bir kısmını gölgelendirici hesaplamanın geri kalanıyla bir araya toplar.

Elbette, modelin doku haritasını uygulamakla aynı şekilde modele yansıtilen görüntüyü uygulayanın bir yolu değildir. Böyle bir şey yaptıysanız, dünyanın yansımaları, yansıma ona yapıştırılmış gibi hareket eder. Yansıma herhangi bir yönden geleyeli, herhangi bir açı için yansıma haritası değeri sağlamanın bir yolunu ve yansıma haritasını dünyaya göre yönlendiren bir yol gerekir. Bu gereksinimleri karşılamak için küpün kenarlarını oluşturmak üzere düzenlenmiş altı doku sağlayan, küp haritası olarak adlandırılan özel bir doku eşlemesi kullanabilirsiniz. Bu küpün içinden bir doku değeri bulmak için herhangi bir yöne işaret edebilirsiniz. Küpün her tarafındaki dokular ortamın görüntülerini içeriyorsa, küpün yüzeyinde doğru konumu örnekleyerek herhangi bir yansımanın benzetimini yapabilirsiniz. Kübü dünyaya hizalı tutarak ortamın doğru bir yansımasını alırsınız. Küpün örneklendiği yeri tespit etmek için, film yüzeyinin yüzeyini yalnızca nesnenin yüzeyi dışına hesaplayıp 3B doku koordinatları olarak kullanırsınız. Küp haritalarını bu şekilde kullanmak, *ortam eşleme* olarak bilinen yaygın bir tekniktir.

Ortam eşleme, önceki paragraflarda açıklandığı şekilde gerçek yansıma malzemelerde etkili bir şekilde bir yaklaşık bakış sağlar. Milbdo topu sahneye daha fazla topraklanmış olmasını sağlayan sanal bir son ek sağlamak için ortam eşlemeli yansımaları gölgelendiricinize karıştırabilirsiniz.

İlk adım, küp harita dokusunu oluşturmaktır. Birçok uygulama türünde küp eşlemesinin içeriği, özellikle de yansıma ince veya ekranda belirgin bir alan kaplayacağından etkili olması gerekmez. Örneğin, birçok oyun, ortam eşleme için önceden hesaplanmış küp haritaları kullanır ve bu, yansımanın doğru olmadığı anlamına gelse de her bir yansıtıcı nesne için en yakın olanı kullanır. Bu, genellikle ikna edici bir etkisi için yeterince iyi bir seçimdir.

### <a name="to-create-textures-for-an-environment-map-by-using-the-image-editor"></a>Görüntü düzenleyicisini kullanarak bir ortam haritası için dokular oluşturmak için

1. Birlikte çalışmak için bir doku oluşturun. Projenize doku ekleme hakkında daha fazla bilgi için bkz. [Görüntü Düzenleyicisi](../designers/image-editor.md)'ndeki Başlarken bölümü.

2. Görüntü boyutunu genişliği yüksekliğine eşit olacak şekilde ayarlayın ve iki boyutlu bir üssü; Bu, küp eşlemesinin dizin oluşturma yöntemi nedeniyle gereklidir. Görüntüyü yeniden boyutlandırmak için, **Özellikler** penceresinde **Genişlik** ve **Yükseklik** özellikleri için yeni değerler belirtin. Örneğin, **Width** ve **Height** özelliklerinin değerini 256 olarak ayarlayın.

3. Dokuyu dolduracak düz bir renk kullanın. Bu doku, milbiard tablosunun yüzeyine karşılık gelen küp eşlemesinin en altında yer alacak. Sonraki doku için kullandığınız rengi göz önünde bulundurun.

4. İlk ile aynı boyutta olan ikinci bir doku oluşturun. Bu doku, bir Milard tablosunun yüzeyine ve taraflarına ve Milard tablo çevresindeki alana karşılık gelen küp eşleminin dört tarafında yinelenir. Alt dokudaki aynı rengi kullanarak bu dokuda Milard tablosunun yüzeyini çizdiğinizden emin olun. Doku şuna benzer görünmelidir:

    ![Küp harita 'in tarafları için doku](../designers/media/gfx_shader_demo_billiard_art_env_texture_side.png)

    Yansıma haritasının etkili olması için photogerçekçi olması gerektiğini unutmayın; Örneğin, bu makaledeki görüntüleri oluşturmak için kullanılan küp eşlemesi altı yerine yalnızca dört cep içerir.

5. Diğer kişilerle aynı boyutta olan üçüncü bir doku oluşturun. Bu doku, Milard tablosunun üzerindeki üst sınıra karşılık gelen küp eşlemesinin en üstü olacaktır. Yansımanın bu bölümünü daha ilginç hale getirmek için, önceki yordamda gölgelendiriciye eklediğiniz yansımalı vurguları daha fazla zorlamak üzere bir ek yük çizebilirsiniz. Doku şuna benzer görünmelidir:

    ![Küp harita 'in üst öğesinin dokusu](../designers/media/gfx_shader_demo_billiard_art_env_texture_top2.png)

   Küp eşlemesinin tarafları için bireysel dokular oluşturduğunuza göre, bunları tek bir *. DDS* dokusundaki depolanabilecek bir küp eşlemesinde birleştirmek için bir araç kullanabilirsiniz. Küp haritasını. DDS doku biçiminde kaydedebir sürece, küp haritasını oluşturmak istediğiniz herhangi bir programı kullanabilirsiniz. Bu izlenecek yol, Haziran, 2010 DirectX SDK 'sının bir parçası olan DirectX doku Aracı kullanılarak nasıl doku oluşturulacağını göstermektedir.

### <a name="to-assemble-a-cube-map-by-using-the-directx-texture-tool"></a>DirectX doku aracını kullanarak bir küp haritasını birleştirmek için

1. DirectX doku aracında, ana menüden **Dosya**  >  **yeni doku**' ı seçin. **Yeni doku** iletişim kutusu görüntülenir.

2. **Doku türü** grubunda, **cubemap dokusunu** seçin.

3. **Boyutlar** grubunda **Genişlik** ve **Yükseklik** için doğru değeri girip **Tamam**' ı seçin. Yeni bir doku belgesi görüntülenir. Varsayılan olarak, doku belgesinde ilk olarak gösterilen doku **pozitif X** küp yüzüne karşılık gelir.

4. Doku küpünün yan tarafında oluşturduğunuz dokuyu küp yüzüne yükleyin. Ana menüde,   >  **Bu cubemap** üzerinde dosya Aç ' ı seçin, küpün yan tarafında oluşturduğunuz dokuyu seçin ve sonra **Aç**' ı seçin.

5. **Negatif X**, **pozitif Z** ve **negatif z** küp yüzleri için 4. adımı yineleyin. Bunu yapmak için, yüklemek istediğiniz yüzü görüntülemeniz gerekir. Farklı bir küp Haritası yüzünü görüntülemek için, ana menüden,   >  **küp haritasını görüntüle yüzeyini** seçin ve ardından görüntülemek istediğiniz yüzü seçin.

6. **Pozitif Y** küp yüzü için, doku küpünün üst kısmında oluşturduğunuz dokuyu yükleyin.

7. **Negatif Y** küp yüzü için, doku küpünün altı için oluşturduğunuz dokuyu yükleyin.

8. Dokuyu kaydedin.

   Küp haritasının yerleşimini şöyle görebilirsiniz:

   ![Ortam küpü eşlemesinin düzeni](../designers/media/gfx_shader_demo_billiard_art_env_texture_top.png)

   Üstteki görüntü pozitif Y (+ Y) küp yüzüdür; Ortadaki, soldan sağa,-X, + Z, + X ve-Z küp yüzleri; En altta-Y küp yüzüdür.

   Şimdi, gölgelendirici geri kalanında küp eşleme örneğini karıştırmak için gölgelendiriciyi değiştirebilirsiniz.

### <a name="to-add-environment-mapping-to-your-shader"></a>Gölgelendiricinize ortam eşlemesi eklemek için

1. Gölgelendiricinizi, ek karıştırma kullanarak ortam eşleme katkısı içerecek şekilde değiştirin. Gölgelendirici grafiğiniz şuna benzemelidir:

    ![Her iki tür yansıtıcı gölgelendirici düğümünün bir kapatması](../designers/media/gfx_shader_demo_billiard_step_4b.png)

    Gölgelendirici grafiğini basitleştirmek için **çarpma-ekleme** düğümü kullanabileceğinizi unutmayın.

    Ortam eşlemeyi uygulayan gölgelendirici düğümlerinin daha ayrıntılı bir görünümü aşağıda verilmiştir:

    ![Ortam eşlemesi eklenmiş Gölgelendirici Grafiği](../designers/media/gfx_shader_demo_billiard_step_4a.png)

2. Küp eşlemesinin doku özelliklerini yapılandırarak önceki yordamda oluşturduğunuz dokuyu uygulayın. **Cubemap örnek** düğümünün **Texture** özelliğinin değerini **Texture2** olarak ayarlayın ve ardından **Texture2** Özellik grubunun **filename** özelliğini kullanarak doku dosyasını belirtin.

3. İsteğe bağlı olarak, **sabit** düğümün **Çıkış** özelliğini yapılandırarak mildo topu reflectivity ayarlayabilirsiniz. Düğümün özelliklerine erişmek için, seçin ve ardından **Özellikler** penceresinde erişmek istediğiniz özelliği bulun.

   Ortam eşleme uygulandığında, milbdo topu şuna benzer görünmelidir:

   ![Ortam eşlenmiş milbdo topu](../designers/media/gfx_shader_demo_billiard_ball_4.png)

   Bu nihai görüntüde, eklediğiniz etkilerin çok ikna edici bir top oluşturmak için bir araya geldiği hakkında dikkat edin. Şekil, doku ve aydınlatma bir 3B nesnenin temel görünümünü oluşturur ve yansımalı önemli noktalar ve yansıtılamalar, Bilardo topunu daha ilgi çekici hale getirir ve ortamının bir parçası gibi görünür.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: gölgelendiriciyi dışarı aktarma](../designers/how-to-export-a-shader.md)
- [Nasıl yapılır. 3B modele gölgelendirici uygulama](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Gölgelendirici Tasarımcısı](../designers/shader-designer.md)
- [Görüntü Düzenleyicisi](../designers/image-editor.md)
- [Gölgelendirici Tasarımcısı düğümleri](../designers/shader-designer-nodes.md)
