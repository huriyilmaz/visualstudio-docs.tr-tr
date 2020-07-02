---
title: 'İzlenecek yol: gerçekçi bir 3B bilardo topu oluşturma'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: af8eb0f3-bf6a-4d1c-ab47-dcd88ab04efa
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4bebaa8c197d0b0a4447739d900062bef2bda37c
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85816663"
---
# <a name="walkthrough-create-a-realistic-3d-billiard-ball"></a>İzlenecek yol: Gerçekçi bir 3B bilardo topu oluşturma

Bu izlenecek yol, Visual Studio 'daki gölgelendirici tasarımcısını ve görüntü düzenleyicisini kullanarak gerçekçi bir 3B mildo topu oluşturmayı gösterir. Milbdo topu 3B görünümü, çeşitli gölgelendirici tekniklerini uygun doku kaynaklarıyla birleştirerek elde edilir.

## <a name="prerequisites"></a>Ön koşullar

Bu yönergeyi tamamlamak için aşağıdaki bileşenler ve beceriler gereklidir:

- Haziran 2010 DirectX SDK 'sına dahil edilen DirectX doku aracı gibi dokuları bir küp haritasına dönüştürmek için bir araç.

- Visual Studio 'da görüntü Düzenleyicisi ile benzerlik.

- Visual Studio 'da gölgelendirici tasarlayıcısıyla benzerlik.

## <a name="create-the-basic-appearance-with-shape-and-texture"></a>Şekil ve doku ile temel görünümü oluşturma

BİLGİSAYAR grafiklerde, en temel görünüm öğeleri şekil ve renklerdir. Bir bilgisayar simülasyonu içinde, gerçek dünyadaki bir nesnenin şeklini temsil eden bir 3B model kullanılması yaygındır. Renk ayrıntısı daha sonra doku eşlemesi kullanılarak modelin yüzeyine uygulanır.

Genellikle, bir sanatçının kullanabileceğiniz bir 3B model oluşturmasını isteyebilirsiniz, ancak milbdo topu ortak bir şekil (Sphere) olduğundan, gölgelendirici tasarımcısının zaten yerleşik olarak bulunan uygun bir modeli vardır.

Sphere, gölgelendirici tasarımcısında varsayılan önizleme şekilsidir; Gölgelendiricinizi önizlemek için şu anda farklı bir şekil kullanıyorsanız sphere öğesine geri dönün.

### <a name="to-preview-the-shader-by-using-a-sphere"></a>Sphere kullanarak gölgelendiriciyi önizlemek için

- Gölgelendirici Tasarımcısı araç çubuğunda **Sphere Ile Önizleme** ' yi seçin.

Sonraki adımda, modele doku uygulayan bir gölgelendirici programı oluşturacaksınız, ancak öncelikle kullanabileceğiniz bir doku oluşturmanız gerekir. Bu izlenecek yol, Visual Studio 'nun bir parçası olan görüntü düzenleyicisini kullanarak dokuyu oluşturmayı gösterir, ancak dokuyu uygun bir biçimde kaydedebilen herhangi bir görüntü düzenleyicisini kullanabilirsiniz.

**Özellikler** penceresinin ve **araç kutusunun** görüntülendiğinden emin olun.

### <a name="to-create-a-billiard-ball-texture-by-using-the-image-editor"></a>Görüntü düzenleyicisini kullanarak milsedo topu dokusu oluşturmak için

1. Birlikte çalışmak için bir doku oluşturun. Projenize doku ekleme hakkında daha fazla bilgi için bkz. [Görüntü Düzenleyicisi](../designers/image-editor.md)'ndeki Başlarken bölümü.

2. Genişliği yüksekliğinin iki katı olacak şekilde görüntü boyutunu ayarlayın; Bu, bir dokunun mildo topu küresel yüzeyiyle eşlenme yöntemi nedeniyle gereklidir. Görüntüyü yeniden boyutlandırmak için, **Özellikler** penceresinde **Genişlik** ve **Yükseklik** özellikleri için yeni değerler belirtin. Örneğin, genişliği 512 ve yüksekliği 256 olarak ayarlayın.

3. Milbdo topu için bir doku çizin ve bir dokunun Sphere üzerinde nasıl eşlendiğine dikkat edin.

    Doku şuna benzer görünmelidir:

    ![Milbdo topu dokusu](../designers/media/gfx_shader_demo_billiard_art_ball_texture.png)

4. İsteğe bağlı olarak, bu dokunun depolama gereksinimlerini azaltmak isteyebilirsiniz. Bunu, yüksekliğinin eşleşmesi için dokunun genişliğini azaltarak yapabilirsiniz. Bu, dokuyu genişliğine göre sıkıştırır, ancak dokunun Sphere ile eşlenme yöntemi nedeniyle mildo topu işlendiğinde genişletilir. Yeniden boyutlandırdıktan sonra doku şuna benzer görünmelidir:

    ![Bir karede sıkıştırılan Milard dokusu](../designers/media/gfx_shader_demo_billiard_art_ball_texture_square.png)

   Şimdi bu dokuyu modele uygulayan bir gölgelendirici oluşturabilirsiniz.

### <a name="to-create-a-basic-texture-shader"></a>Temel doku gölgelendiricisi oluşturmak için

1. Çalışmak için bir DGSL gölgelendiricisi oluşturun. Projenize bir DGSL gölgelendiricisi ekleme hakkında daha fazla bilgi için bkz. [gölgelendirici tasarımcısında](../designers/shader-designer.md)Başlarken bölümü.

    Varsayılan olarak, bir gölgelendirici grafiği şöyle görünür:

    ![Varsayılan Gölgelendirici Grafiği](../designers/media/gfx_shader_demo_billiard_step_0.png)

2. Varsayılan gölgelendiriciyi, bir doku örneğinin değerini geçerli piksele uygulanacak şekilde değiştirin. Gölgelendirici Grafiği şöyle görünmelidir:

    ![Bir nesneye doku uygulayan Gölgelendirici Grafiği](../designers/media/gfx_shader_demo_billiard_step_1.png)

3. Doku özelliklerini yapılandırarak önceki yordamda oluşturduğunuz dokuyu uygulayın. **Doku örneği** düğümünün **doku** özelliğinin değerini **Doku1**olarak ayarlayın ve ardından aynı özellik penceresinde **Doku1** Property grubunun **filename** özelliğini kullanarak doku dosyasını belirtin.

   Gölgelendiricinize doku uygulama hakkında daha fazla bilgi için bkz. [nasıl yapılır: temel doku gölgelendiricisi oluşturma](../designers/how-to-create-a-basic-texture-shader.md).

   Milbdo topu artık şuna benzer görünmelidir:

   ![Dokulu mildo topu 'nın bir kapatması](../designers/media/gfx_shader_demo_.png)

## <a name="create-depth-with-the-lambert-lighting-model"></a>Lambert aydınlatma modeliyle derinlik oluşturma

Şimdiye kadar, kolayca tanınabilir bir milbdo topu oluşturdunuz. Bununla birlikte, düz ve ilginç olmayan bir şekilde görünür. bir milde, bir milde bir çoğaltmayla bir Biard topu resmine benzer. Bilardo topu yüzeyindeki her bir pikselin aynı ışık miktarını alıp aldığına benzer şekilde davranan, düz görünüm, uyarlaması gölgelendiriciden elde olur.

Gerçek dünyada, ışık doğrudan bir açık kaynak sunan yüzeyler üzerinde en parlak test ve ışık kaynağına eğik açılı olan yüzeyler üzerinde daha az parlak bir şekilde görünür. Bunun nedeni, açık ışındaki enerji, yüzey doğrudan ışık kaynağına doğru yüzlü en küçük yüzey alanına dağıtılır. Yüzey, ışık kaynağından uzakta olduğu için, aynı enerji miktarı giderek daha büyük bir yüzey alanı üzerinden dağıtılır. Bir ışık kaynağından uzaklaşan bir yüzey hiç hafif bir enerji almaz ve tamamen koyu bir görünüme neden olur. Bir nesnenin yüzeyi genelinde parlaklığın varyansı, bir nesnenin şeklini göstermeye yardımcı olan önemli bir görsel destesi; Bu olmadan, nesne düz görünür.

BİLGİSAYAR grafiklerde, *aydınlatma modelleri*— karmaşık, gerçek dünya aydınlatma etkileşimlerinin basitleştirilmesi, gerçek dünya ışıksının görünümünü çoğaltmak için kullanılır. Lambert aydınlatma modeli, önceki paragrafta açıklandığı gibi, bir nesnenin yüzeyi genelinde dağıtılmış olan ışık miktarını değiştirir. Milbdo topu daha ikna edici bir 3B görünümü sağlamak için gölgelendiricinize Lambert aydınlatma modeli ekleyebilirsiniz.

### <a name="to-add-lambert-lighting-to-your-shader"></a>Gölgelendiricinize Lambert aydınlatma eklemek için

- Gölgelendiricinizi, Lambert aydınlatma değeri ile doku örneğinin değerini modüle olacak şekilde değiştirin. Gölgelendirici grafiğiniz şuna benzemelidir:

   ![Lambert aydınlatma eklenmiş Gölgelendirici Grafiği](../designers/media/gfx_shader_demo_billiard_step_2.png)

- İsteğe bağlı olarak, gölgelendirici grafiğinin **Materialdağıt** özelliğini yapılandırarak aydınlatmanın nasıl davranacağını ayarlayabilirsiniz. Gölgelendirici grafiğinin özelliklerine erişmek için tasarım yüzeyinde boş bir alan seçin ve ardından **Özellikler** penceresinde erişmek istediğiniz özelliği bulun.

Gölgelendiricinize Lambert aydınlatmanın nasıl uygulanacağı hakkında daha fazla bilgi için bkz. [nasıl yapılır: temel Lambert gölgelendiricisi oluşturma](../designers/how-to-create-a-basic-lambert-shader.md).

Lambert aydınlatma uygulanmış olarak, milbdo topu şuna benzer görünmelidir:

![Dokulu ve aydınlatmalı bilardo topu](../designers/media/gfx_shader_demo_billiard_ball_2.png)

## <a name="enhance-the-basic-appearance-with-specular-highlights"></a>Yansımalı vurgularla temel görünümü geliştirin

Lambert aydınlatma modeli, yalnızca doku gölgelendiricide bulunmayan şekil ve boyutun anlamlı olmasını sağlar. Ancak, milbdo topunun hala biraz görünümü vardır.

Gerçek bir mildo topu genellikle ışığın bir kısmını yansıtan parlak bir sontır. Bu yansıtılan ışığın bazıları, bir yüzeyin yansıtma özelliklerinin benzetimini yaparak yansımalı vurgularda sonuçlanır. Son özelliklere bağlı olarak, vurgular yerelleştirilmiş veya geniş, yoğun veya hafif olabilir. Bu yansımalı yansımalar, bir ışık kaynağı, yüzey yönü ve kamera konumu arasındaki ilişki kullanılarak modellenir; Yani, yüzey yönü doğrudan kameraya yansıtıldığınızda vurgu en yoğun olur ve yansıma daha az doğrudan olduğunda daha az yoğun olur.

Phong aydınlatma modeli, önceki paragrafta açıklandığı gibi yansımalı vurguları dahil etmek için Lambert aydınlatma modeli üzerinde oluşturulur. Milbdo topu, daha ilgi çekici bir görünüm elde eden bir sanal bitiş sağlamak için, gölgelendirici için Phong aydınlatma modelini ekleyebilirsiniz.

### <a name="to-add-specular-highlights-to-your-shader"></a>Gölgelendiricinize yansımalı vurgular eklemek için

1. Gölgelendiricinizi, ek karıştırma kullanarak yansımalı katkı içerecek şekilde değiştirin. Gölgelendirici grafiğiniz şuna benzemelidir:

    ![Yansımalı aydınlatma eklenen Gölgelendirici Grafiği](../designers/media/gfx_shader_demo_billiard_step_3.png)

2. İsteğe bağlı olarak, gölgelendirici grafiğinin yansımalı özelliklerini (**materialspecsel** ve **MaterialSpecularPower**) yapılandırarak, yansımalı vurgulamanın nasıl davranacağını ayarlayabilirsiniz. Gölgelendirici grafiğinin özelliklerine erişmek için tasarım yüzeyinde boş bir alan seçin ve **Özellikler** penceresinde erişmek istediğiniz özelliği bulun.

   Gölgelendiricinize yansımalı vurguların nasıl uygulanacağı hakkında daha fazla bilgi için bkz. [nasıl yapılır: temel bir Phong gölgelendiricisi oluşturma](../designers/how-to-create-a-basic-phong-shader.md).

   Yansımalı vurgulamanın uygulanmış olması, milbdo topu şuna benzer görünmelidir:

   ![Bilardo topu, yansımalı olarak eklendi](../designers/media/gfx_shader_demo_billiard_ball_3.png)

## <a name="create-a-sense-of-space-by-reflecting-the-environment"></a>Ortamı yansıtarak alan hissi oluşturma

Lekelsel açıktonlar uygulandıktan sonra, milbdo topu oldukça ikna edici görünüyor. Doğru şekil, doğru boyama işi ve sağ bitiş. Ancak, milbdo topunun, ortamının bir parçası gibi daha fazla görünmesini sağlayacak bir teknik de daha vardır.

Gerçek bir milyardo topu yakından incelerseniz parlak yüzeyinin yalnızca yansımalı vurgular sergilemediğini, ancak dünyanın her yerindeki dünyanın bir görüntüsünü daha da yansıttığını görebilirsiniz. Bu yansımanın benzetimini, bir doku olarak ortamın bir görüntüsünü kullanarak ve her pikselin son rengini belirleyebilmek için modelin kendi dokusuyla birleştirerek benzeleyebilirsiniz. İstediğiniz bitiş türüne bağlı olarak, yansıma dokusunun daha fazlasını veya daha azını, gölgelendirici geri kalanı ile birlikte birleştirebilirsiniz. Örneğin, bir yansıtma gibi yüksek oranda yansıtmalı bir yüzeyi taklit eden bir gölgelendirici yalnızca yansıma dokusunu kullanabilir, ancak bir milde bulunan bir bilardo topu gibi daha hafif bir yansımaya benzetim yapan bir gölgelendirici, yalnızca yansıma dokusunun değerinin küçük bir kısmını, gölgelendirici hesaplamasının geri kalanı ile birleştirebilirler.

Tabii ki, yansıtılan görüntüyü modelin doku haritasını uyguladığınız şekilde modele uygulamanız yeterlidir. Bunu yaptıysanız, dünyanın yansıması, yansıma kendisine tutkallanır gibi mildo topu ile hareket edecektir. Bir yansıma herhangi bir yönden gelebileceğinden, herhangi bir açıda yansıma eşleme değeri sağlamak için bir yol ve yansıma haritasını dünyaya göre yönlendirmeye tutmanın bir yolu vardır. Bu gereksinimleri karşılamak için, küpün yüzlerini oluşturmak üzere düzenlenmiş altı doku sağlayan, *küp Haritası*adı verilen özel bir doku eşlemi türü kullanabilirsiniz. Bu küpün içinden bir doku değeri bulmak için herhangi bir yöne işaret edebilirsiniz. Küpün her tarafındaki dokular ortamın görüntülerini içeriyorsa, küpün yüzeyinde doğru konumu örnekleyerek herhangi bir yansımanın benzetimini yapabilirsiniz. Kübü dünyaya hizalı tutarak ortamın doğru bir yansımasını alırsınız. Küpün örneklendiği yeri tespit etmek için, film yüzeyinin yüzeyini yalnızca nesnenin yüzeyi dışına hesaplayıp 3B doku koordinatları olarak kullanırsınız. Küp haritalarını bu şekilde kullanmak, *ortam eşleme*olarak bilinen yaygın bir tekniktir.

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

2. **Doku türü** grubunda, **cubemap dokusunu**seçin.

3. **Boyutlar** grubunda **Genişlik** ve **Yükseklik**için doğru değeri girip **Tamam**' ı seçin. Yeni bir doku belgesi görüntülenir. Varsayılan olarak, doku belgesinde ilk olarak gösterilen doku **pozitif X** küp yüzüne karşılık gelir.

4. Doku küpünün yan tarafında oluşturduğunuz dokuyu küp yüzüne yükleyin. Ana menüde, **File**  >  **Bu cubemap**üzerinde dosya Aç ' ı seçin, küpün yan tarafında oluşturduğunuz dokuyu seçin ve sonra **Aç**' ı seçin.

5. **Negatif X**, **pozitif Z**ve **negatif z** küp yüzleri için 4. adımı yineleyin. Bunu yapmak için, yüklemek istediğiniz yüzü görüntülemeniz gerekir. Farklı bir küp Haritası yüzünü görüntülemek için, ana menüden, **View**  >  **küp haritasını görüntüle yüzeyini**seçin ve ardından görüntülemek istediğiniz yüzü seçin.

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

2. Küp eşlemesinin doku özelliklerini yapılandırarak önceki yordamda oluşturduğunuz dokuyu uygulayın. **Cubemap örnek** düğümünün **Texture** özelliğinin değerini **Texture2**olarak ayarlayın ve ardından **Texture2** Özellik grubunun **filename** özelliğini kullanarak doku dosyasını belirtin.

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
