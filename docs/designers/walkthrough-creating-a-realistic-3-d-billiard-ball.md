---
title: 'Walkthrough: Gerçekçi bir 3D Bilardo Topu Oluşturma'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: af8eb0f3-bf6a-4d1c-ab47-dcd88ab04efa
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 866f91303c224f8330a4d2be76f3d29331fcb346
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589922"
---
# <a name="walkthrough-create-a-realistic-3d-billiard-ball"></a>Gerçekçi bir 3B bilardo topu oluşturma

Bu yürüyüş, Visual Studio'da Shader Designer ve Image Editor'u kullanarak gerçekçi bir 3D bilardo topu nun nasıl oluşturulacak larını gösterir. Bilardo topunun 3Boyutlu görünümü, çeşitli gölgeleme tekniklerini uygun doku kaynaklarıyla birleştirerek elde edilir.

## <a name="prerequisites"></a>Önkoşullar

Bu izbiyi tamamlamak için aşağıdaki bileşenlere ve becerilere ihtiyacınız vardır:

- Haziran 2010 DirectX SDK'da bulunan DirectX Doku Aracı gibi dokuları küp eşleme aracı için bir araçtır.

- Visual Studio'daki Görüntü Editörü'ne aşinalık.

- Visual Studio'da Shader Tasarımcısı'na aşinalık.

## <a name="create-the-basic-appearance-with-shape-and-texture"></a>Şekil ve doku ile temel görünümü oluşturun

Bilgisayar grafiklerinde, görünümün en temel öğeleri şekil ve renktir. Bir bilgisayar simülasyonunda, gerçek bir nesnenin şeklini temsil etmek için bir 3B model kullanmak yaygındır. Renk ayrıntısı daha sonra bir doku eşlemi kullanılarak modelin yüzeyine uygulanır.

Genellikle, bir sanatçıdan kullanabileceğiniz bir 3B model oluşturmasını istemeniz gerekebilir, ancak bilardo topu ortak bir şekil (küre) olduğundan, Shader Designer'ın zaten yerleşik uygun bir modeli vardır.

Küre, Shader Designer'daki varsayılan önizleme şeklidir; Gölgeleyicinizi önizlemek için şu anda farklı bir şekil kullanıyorsanız, küreye geri dön.

### <a name="to-preview-the-shader-by-using-a-sphere"></a>Bir küre kullanarak gölgeyi önizlemek için

- Shader Designer araç çubuğunda **küreyle Önizleme'yi seçin.**

Bir sonraki adımda, modele doku uygulayan bir gölgeli program oluşturursunuz, ancak önce kullanabileceğiniz bir doku oluşturmanız gerekir. Bu izlenebilirlik, Visual Studio'nun bir parçası olan Görüntü Düzenleyicisi'ni kullanarak dokunun nasıl oluşturulabileceğini gösterir, ancak dokuyu uygun biçimde kaydedebilirsiniz herhangi bir görüntü düzenleyicisini kullanabilirsiniz.

**Özellikler** penceresinin ve **Araç Kutusunun** görüntülendiğinden emin olun.

### <a name="to-create-a-billiard-ball-texture-by-using-the-image-editor"></a>Görüntü Düzenleyicisi'ni kullanarak bilardo topu dokusu oluşturmak için

1. Çalışmak için bir doku oluşturun. Projenize nasıl doku ekleyeceğiniz hakkında bilgi için Resim Düzenleyicisi'ndeki Başlarken bölümüne bakın. [Image Editor](../designers/image-editor.md)

2. Görüntü boyutunu, genişliğinin yüksekliğinin iki katı olacak şekilde ayarlayın; bir dokunun bilardo topunun küresel yüzeyine eşlenme şeklinden dolayı bu gereklidir. Görüntüyü yeniden boyutlandırmak için **Özellikler** penceresinde, **Genişlik** ve **Yükseklik** özellikleri için yeni değerler belirtin. Örneğin, genişliği 512'ye, yüksekliği 256'ya ayarlayın.

3. Bilardo topu için bir doku çizin, bir dokunun küreüzerine nasıl eşlenedildiğini aklınızda bulundurun.

    Doku buna benzer olmalıdır:

    ![Bilardo topu için doku](../designers/media/gfx_shader_demo_billiard_art_ball_texture.png)

4. İsteğe bağlı olarak, bu dokunun depolama gereksinimlerini azaltmak isteyebilirsiniz. Bunu, dokunun yüksekliğe uyacak şekilde genişliğini azaltarak yapabilirsiniz. Bu, dokuyu genişliği boyunca sıkıştırır, ancak dokunun küreye eşlenme şekli nedeniyle, bilardo topu işlendiğinde genişletilir. Yeniden boyutlandırmasonra, doku şuna benzer olmalıdır:

    ![Bilardo dokusu bir kare içine sıkıştırılmış](../designers/media/gfx_shader_demo_billiard_art_ball_texture_square.png)

   Şimdi, bu dokuyu modele uygulayan bir gölgeoluşturabilirsiniz.

### <a name="to-create-a-basic-texture-shader"></a>Temel doku shader oluşturmak için

1. Çalışmak için bir DGSL gölgeleyici oluşturun. Projenize DGSL shader nasıl ekleyeceğiniz hakkında bilgi [için, Shader Designer'daki](../designers/shader-designer.md)Başlarken bölümüne bakın.

    Varsayılan olarak, bir gölgeli grafik şuna benzer:

    ![Varsayılan gölgeli grafiği](../designers/media/gfx_shader_demo_billiard_step_0.png)

2. Varsayılan gölgeleyiciyi, doku örneğinin değerini geçerli piksele uygulayacak şekilde değiştirin. Gölgeli grafiği aşağıdaki gibi görünmelidir:

    ![Bir nesneye doku uygulayan gölgeli grafik](../designers/media/gfx_shader_demo_billiard_step_1.png)

3. Doku özelliklerini yapılandırarak önceki yordamda oluşturduğunuz dokuyu uygulayın. **Doku Örneği** düğümünün **Doku** özelliğinin değerini **Texture1'e**ayarlayın ve ardından **doku1** özellik grubunun **Dosya Adı** özelliğini aynı özellik penceresinde kullanarak doku dosyasını belirtin.

   Gölgelinizde bir doku nasıl uygulanacağı hakkında daha fazla bilgi için [bkz.](../designers/how-to-create-a-basic-texture-shader.md)

   Bilardo topu şimdi bu benzer görünmelidir:

   ![Dokulu bilardo topunun yakın çekim](../designers/media/gfx_shader_demo_.png)

## <a name="create-depth-with-the-lambert-lighting-model"></a>Lambert aydınlatma modeli ile derinlik oluşturun

Şimdiye kadar kolayca tanınabilir bir bilardo topu yarattınız. Ancak, düz ve ilginç görünür-daha ikna edici bir çoğaltma daha bir bilardo topu bir karikatür resmi gibi. Düz görünüm, bilardo topunun yüzeyindeki her piksel aynı miktarda ışık alıyormuş gibi görünen basit gölgeleyiciden kaynaklanır.

Gerçek dünyada, ışık doğrudan bir ışık kaynağına dönük yüzeylerde en parlak görünür ve ışık kaynağına eğik bir açıda olan yüzeylerde daha az parlak görünür. Bunun nedeni, ışık ışınlarındaki enerjinin, yüzey doğrudan ışık kaynağına dönük olduğunda en küçük yüzey alanına dağılmış olmasıdır. Yüzey ışık kaynağından uzaklaştıkça, aynı miktarda enerji giderek daha büyük bir yüzey alanına dağılır. Bir ışık kaynağından uzağa bakan bir yüzey hiç ışık enerjisi almaz, bu da tamamen karanlık bir görünüme neden olabilir. Bir nesnenin yüzeyindeki parlaklıktaki bu fark, nesnenin şeklini göstermeye yardımcı olan önemli bir görsel işarettir; onsuz, nesne düz görünür.

Bilgisayar grafiklerinde, *aydınlatma modelleri*(karmaşık, gerçek dünya aydınlatma etkileşimlerinin basitleştirilmiş yaklaşımları) gerçek ışıklandırma görünümünü çoğaltmak için kullanılır. Lambert aydınlatma modeli, önceki paragrafta açıklandığı gibi, bir nesnenin yüzeyinde yaygın olarak yansıyan ışık miktarını değişir. Bilardo topuna daha ikna edici bir 3D görünüm kazandırmak için shader'ınıza Lambert aydınlatma modelini ekleyebilirsiniz.

### <a name="to-add-lambert-lighting-to-your-shader"></a>Shader'ınıza Lambert aydınlatması eklemek için

- Lambert aydınlatma değerine göre doku örneğinin değerini modüle etmek için gölgeleyicinizi değiştirin. Gölgeli grafiğiniz şu na benzemelidir:

   ![Lambert aydınlatmalı shader grafiği eklendi](../designers/media/gfx_shader_demo_billiard_step_2.png)

- İsteğe bağlı olarak, gölgeli grafiğin **MaterialDiffuse** özelliğini yapılandırarak aydınlatmanın nasıl bir şekilde nasıl olduğunu ayarlayabilirsiniz. Gölgeli grafiğin özelliklerine erişmek için tasarım yüzeyinin boş bir alanını seçin ve ardından **Özellikler** penceresinde erişmek istediğiniz özelliği bulun.

Shader'Inizde Lambert aydınlatmasını nasıl uygulayacağıhakkında daha fazla bilgi için [bkz.](../designers/how-to-create-a-basic-lambert-shader.md)

Lambert aydınlatma uygulandığında, bilardo topu bu benzer görünmelidir:

![Dokulu ve aydınlatılmış bilardo topunun yakın çekim](../designers/media/gfx_shader_demo_billiard_ball_2.png)

## <a name="enhance-the-basic-appearance-with-specular-highlights"></a>Aynasal vurgularla temel görünümü geliştirin

Lambert aydınlatma modeli, yalnızca doku gölgelisinde bulunmayan şekil ve boyut duygusunu sağlar. Ancak, bilardo topu hala biraz sıkıcı bir görünüme sahiptir.

Gerçek bir bilardo topu genellikle üzerine düşen ışığın bir kısmını yansıtan parlak bir yüzeyvardır. Bu yansıyan ışık sonuçlarının bir yüzeyi yansıtan özellikleri taklit aynasal vurgular. Bitiş özelliklerine bağlı olarak, vurgular yerelleştirilmiş veya geniş, yoğun veya ince olabilir. Bu aynasal yansımalar bir ışık kaynağı, yüzeyin yönü ve kamera konumu arasındaki ilişki kullanılarak modellenir- yani, yüzeyin yönü ışık kaynağını doğrudan ışık kaynağına yansıttığında vurgu en yoğun ve yansıma daha az doğrudan olduğunda daha az yoğundur.

Phong aydınlatma modeli lambert aydınlatma modeli üzerinde bir önceki paragrafta açıklandığı gibi aynasal vurgular içerecek şekilde inşa eder. Bilardo topu daha ilginç bir görünüm sonuçları simüle bitirmek vermek için gölgeli için Phong aydınlatma modeli ekleyebilirsiniz.

### <a name="to-add-specular-highlights-to-your-shader"></a>Gölgelinize aynasal vurgular eklemek için

1. Katkı maddesi karıştırma kullanarak aynasal katkıyı içerecek şekilde gölgeleyicinizi değiştirin. Gölgeli grafiğiniz şu na benzemelidir:

    ![Aynasal aydınlatmalı shader grafiği eklendi](../designers/media/gfx_shader_demo_billiard_step_3.png)

2. İsteğe bağlı olarak, shader grafiğin aynasal özelliklerini **(MaterialSpecular ve MaterialSpecularPower)** yapılandırarak aynasal vurgunun nasıl bir şekilde nasıl olduğunu ayarlayabilirsiniz. **MaterialSpecularPower** Gölgeli grafiğin özelliklerine erişmek için tasarım yüzeyinin boş bir alanını seçin ve ardından **Özellikler** penceresinde erişmek istediğiniz özelliği bulun.

   Gölgelinizde aynasal vurgular nasıl uygulanacağı hakkında daha fazla bilgi için [bkz.](../designers/how-to-create-a-basic-phong-shader.md)

   Uygulanan aynasal vurgulama ile, bilardo topu bu benzer görünmelidir:

   ![Bilardo topunun aynalı ile yakın çekim eklendi](../designers/media/gfx_shader_demo_billiard_ball_3.png)

## <a name="create-a-sense-of-space-by-reflecting-the-environment"></a>Çevreyi yansıtarak bir alan duygusu yaratmak

Uygulanan aynasal vurgular ile, bilardo topu oldukça ikna edici görünüyor. Doğru şekle, doğru boya işine ve doğru kaplamaya sahiptir. Ancak, bilardo topu daha çevrenin bir parçası gibi görünmesini sağlayacak bir teknik daha var.

Gerçek bir bilardo topunu yakından incelerseniz, parlak yüzeyinin sadece aynasal vurgular sergilemediğini, aynı zamanda etrafındaki dünyanın görüntüsünü de hafifçe yansıttığını görebilirsiniz. Bu yansımayı, ortamın bir görüntüsünü doku olarak kullanarak ve her pikselin son rengini belirlemek için modelin kendi dokusuyla birleştirerek simüle edebilirsiniz. İstediğiniz bitiş türüne bağlı olarak, yansıma dokusunun daha fazla veya daha azını gölgelinin geri kalanıyla birleştirebilirsiniz. Örneğin, ayna gibi son derece yansıtıcı bir yüzeyi simüle eden bir gölge, yalnızca yansıma dokusunu kullanabilir, ancak bilardo topunda bulunan gibi daha ince bir yansımayı simüle eden bir gölge, yansımanın sadece küçük bir kısmını birleştirebilir shader hesaplama geri kalanı ile birlikte doku değeri.

Tabii ki, yansıtılan görüntüyü modelin doku eşlemasını uyguladığınız şekilde uygulayamazsınız. Eğer olsaydı, dünyanın yansıması sanki yansıması ona yapıştırılmış gibi bilardo topu ile hareket edecekti. Bir yansıma herhangi bir yönden gelebildiği için, herhangi bir açı için bir yansıma haritası değeri sağlamanın bir yolunu ve yansıma haritasını dünyaya göre yönlendirmenin bir yolunu tutmanız gerekir. Bu gereksinimleri karşılamak için küpün kenarlarını oluşturacak şekilde düzenlenmiş altı doku sağlayan *küp eşlemi*adı verilen özel bir tür doku eşlemi kullanabilirsiniz. Bu küpün içinden, bir doku değeri bulmak için herhangi bir yönde işaret edebilirsiniz. Küpün her iki tarafındaki dokular ortamın görüntülerini içeriyorsa, küpün yüzeyindedoğru konumu örnekleyerek herhangi bir yansımayı simüle edebilirsiniz. Küpü dünyaya hizalayarak, çevrenin doğru bir yansımasını elde elabilirsiniz. Küpün nerede örnekleneceğin nerede olduğunu belirlemek için, kamera vektörünün nesnenin yüzeyindeki yansımasını hesaplar ve ardından 3B doku koordinatları olarak kullanabilirsiniz. Küp eşlemlerini bu şekilde *kullanmak, çevre eşleme*olarak bilinen yaygın bir tekniktir.

Çevre eşleme, önceki paragraflarda açıklandığı gibi gerçek yansımaların etkin bir yaklaşım sağlar. Bilardo topuna, bilardo topunun sahnede daha topraklanmış görünmesini sağlayan simüle edilmiş bir yüzey vermek için gölgenize ortam eşlenmiş yansımaları karıştırabilirsiniz.

İlk adım bir küp eşlemi dokusu oluşturmaktır. Birçok uygulama türünde, küp eşencenin içeriğinin etkili olması için mükemmel olması gerekmez, özellikle yansıma ince sayılsa veya ekranda belirgin bir alan kaplamadığında. Örneğin, birçok oyun ortam eşleme için önceden hesaplanmış küp eşlemleri kullanır ve yansımanın doğru olmadığı anlamına gelse de, her yansıtıcı nesneye en yakın olanı kullanır. Hatta kaba bir yaklaşım genellikle ikna edici bir etki için yeterince iyi.

### <a name="to-create-textures-for-an-environment-map-by-using-the-image-editor"></a>Görüntü Düzenleyicisi'ni kullanarak ortam haritası için dokular oluşturmak için

1. Çalışmak için bir doku oluşturun. Projenize nasıl doku ekleyeceğiniz hakkında bilgi için Resim Düzenleyicisi'ndeki Başlarken bölümüne bakın. [Image Editor](../designers/image-editor.md)

2. Görüntü boyutunu, genişliği yüksekliğine eşit olacak ve iki boyutu olacak şekilde ayarlayın; bu, küp eşleminin dizine eklenme şekli nedeniyle gereklidir. Görüntüyü yeniden boyutlandırmak için **Özellikler** penceresinde, **Genişlik** ve **Yükseklik** özellikleri için yeni değerler belirtin. Örneğin, **Genişlik** ve **Yükseklik** özelliklerinin değerini 256 olarak ayarlayın.

3. Dokuyu doldurmak için düz bir renk kullanın. Bu doku, bilardo tablosunun yüzeyine karşılık gelen küp haritasının alt kısmı olacaktır. Bir sonraki doku için kullandığınız rengi aklınızda tutun.

4. İlkiyle aynı boyutta ikinci bir doku oluşturun. Bu doku, bilardo masasının yüzeyine ve yanlarına karşılık gelen küp haritasının dört tarafında ve bilardo masasının çevresindeki alana tekrarlanır. Alt dokudaki yle aynı rengi kullanarak bu dokudaki bilardo masasının yüzeyini çizdiğinden emin olun. Doku buna benzer olmalıdır:

    ![Küp eşliliğin kenarları için doku](../designers/media/gfx_shader_demo_billiard_art_env_texture_side.png)

    Bir yansıma haritasının etkili olması için fotogerçekçi olması gerekmediğini unutmayın; örneğin, bu makaledeki görüntüleri oluşturmak için kullanılan küp eşlemi altı yerine yalnızca dört cep içerir.

5. Diğerleriyle aynı boyutta üçüncü bir doku oluşturun. Bu doku, bilardo masasının üzerindeki tavana karşılık gelen küp haritasının üst kısmı olacaktır. Yansımanın bu kısmını daha ilginç hale getirmek için, önceki yordamda gölgeye eklediğiniz aynasal vurguları güçlendirmek için havai bir ışık çizebilirsiniz. Doku buna benzer olmalıdır:

    ![Küp eşliliğin üst kısmı için doku](../designers/media/gfx_shader_demo_billiard_art_env_texture_top2.png)

   Artık küp eşleminin kenarları için tek tek dokular oluşturduğunuza göre, bunları tek bir *.dds* dokusunda depolanabilecek bir küp eşlemi halinde birleştirmek için bir araç kullanabilirsiniz. Küp eşlesini .dds doku biçiminde kaydedebileceği sürece küp eşlemi oluşturmak istediğiniz herhangi bir programı kullanabilirsiniz. Bu gözden geçirme, Haziran 2010 DirectX SDK'nın bir parçası olan DirectX Doku Aracı'nı kullanarak dokunun nasıl oluşturulabildiğini gösterir.

### <a name="to-assemble-a-cube-map-by-using-the-directx-texture-tool"></a>DirectX Doku Aracı'nı kullanarak küp eşlemi oluşturmak için

1. DirectX Doku Aracı'nda, ana menüde**Yeni Doku** **Dosyası'nı** > seçin. **Yeni Doku** iletişim kutusu görüntülenir.

2. Doku **Türü** grubunda **Küp Eşkenar Laksat'ı**seçin.

3. **Boyutlar** grubunda, **Genişlik** ve **Yükseklik**için doğru değeri girin ve sonra **Tamam'ı**seçin. Yeni bir doku belgesi görüntülenir. Varsayılan olarak, doku belgesinde ilk olarak gösterilen doku **Pozitif X** küpyüz karşılık gelir.

4. Doku küpünün yan tarafı için oluşturduğunuz dokuyu küp yüzüne yükleyin. Ana menüde, **Bu** > Küp Yüz Üzerine Dosya**Aç'ı**seçin, küpün yan tarafı için oluşturduğunuz dokuyu seçin ve ardından **Aç'ı**seçin.

5. **Negatif X,** **Pozitif Z**ve Negatif **Z** küpyüzleri için adım 4'ü tekrarlayın. Bunu yapmak için, yüklemek istediğiniz yüzü görüntülemeniz gerekir. Ana menüde farklı bir küp eşlemi yüzü görüntülemek için**Küp Eş Yüzünü** **Görüntüle'yi** > seçin ve ardından görüntülemek istediğiniz yüzü seçin.

6. Pozitif **Y** küpü yüzü için, doku küpünün üst kısmı için oluşturduğunuz dokuyu yükleyin.

7. Negatif **Y** küpyüzü için, doku küpünün alt kısmı için oluşturduğunuz dokuyu yükleyin.

8. Dokuyu kaydedin.

   Küp haritasının düzenini şöyle tahmin edebilirsiniz:

   ![Çevre küpü haritasının düzeni](../designers/media/gfx_shader_demo_billiard_art_env_texture_top.png)

   Üstteki görüntü pozitif Y (+Y) küp yüzüdür; ortada, soldan sağa, -X, +Z, +X ve -Z küp yüzleri; en altta -Y küp yüzü dür.

   Şimdi shader'ı küp eşlem örneğini gölgeleyicinin geri kalanına karıştırmak için değiştirebilirsiniz.

### <a name="to-add-environment-mapping-to-your-shader"></a>Gölgeleme cihazınıza ortam eşlemi eklemek için

1. Gölgeleyicinizi, katkı maddesi karıştırma kullanarak ortam eşleme katkısını içerecek şekilde değiştirin. Gölgeli grafiğiniz şu na benzemelidir:

    ![Yansıtıcı gölgeli düğümlerin her iki tür bir yakın çekim](../designers/media/gfx_shader_demo_billiard_step_4b.png)

    Gölgeli grafiği basitleştirmek için **Çarpım-Ekle** düğümlerini kullanabileceğinizi unutmayın.

    Burada, ortam eşlemi uygulayan gölgeli düğümlerin daha ayrıntılı bir görünümü vereyim:

    ![Ortam eşlemeli gölgeli grafik eklendi](../designers/media/gfx_shader_demo_billiard_step_4a.png)

2. Küp eşlemindoku özelliklerini yapılandırarak önceki yordamda oluşturduğunuz dokuyu uygulayın. **Küp Eşlem Örnek** düğümünün **Doku** özelliğinin **değerini Texture2'ye**ayarlayın ve **ardından Texture2** özellik grubunun **Dosya Adı** özelliğini kullanarak doku dosyasını belirtin.

3. İsteğe bağlı olarak, **Sabit** düğümün **Çıkış** özelliğini yapılandırarak bilardo topunun yansıtıcılığını ayarlayabilirsiniz. Düğümün özelliklerine erişmek için düğümü seçin ve ardından **Özellikler** penceresinde erişmek istediğiniz özelliği bulun.

   Uygulanan ortam haritalaması yla, bilardo topunuzun buna benzer görünmesi gerekir:

   ![Çevrenin yakın çekim bilardo topu eşlenen](../designers/media/gfx_shader_demo_billiard_ball_4.png)

   Bu son resimde, eklediğiniz efektlerin çok ikna edici bir bilardo topu oluşturmak için nasıl bir araya geldiğine dikkat edin. Şekil, doku ve aydınlatma bir 3B nesnenin temel görünümünü oluşturmak, ve aynasal vurgular ve yansımaları bilardo topu daha ilginç hale ve ortamının bir parçası gibi görünüyorsun.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Gölgeli dışa aktarma](../designers/how-to-export-a-shader.md)
- [Nasıl yapılır. 3B modele gölgelendirici uygulama](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Shader Tasarımcısı](../designers/shader-designer.md)
- [Görüntü Düzenleyici](../designers/image-editor.md)
- [Gölgeli Tasarımcı düğümleri](../designers/shader-designer-nodes.md)
