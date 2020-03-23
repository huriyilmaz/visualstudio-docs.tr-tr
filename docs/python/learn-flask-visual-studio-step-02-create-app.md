---
title: Visual Studio adım 2, görünümler ve şablonlar Flask öğretici öğrenin
titleSuffix: ''
description: Visual Studio projeleri bağlamında Flask temellerinin bir walkthrough, özellikle bir uygulama oluşturma adımları ve görünümler ve şablonlar kullanarak.
ms.date: 01/07/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 03a0eb6808b2298e0727492978d9beb7cfaf2216
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "79302842"
---
# <a name="step-2-create-a-flask-app-with-views-and-page-templates"></a>Adım 2: Görünümler ve sayfa şablonları içeren bir Flask uygulaması oluşturma

**Önceki adım: [Visual Studio projesi ve çözümü oluşturma](learn-flask-visual-studio-step-01-project-solution.md)**

Bu öğretici adım 1 ne var bir sayfa ve tek bir dosyada tüm kod ile bir Flask uygulamasıdır. Gelecekteki geliştirmeye izin vermek için, kodu yeniden düzenlemek ve sayfa şablonları için bir yapı oluşturmak en iyisidir. Özellikle, uygulamanın görünümleri için kodu başlangıç kodu gibi diğer yönlerden ayırmak istiyorsunuz.

Bu adımda şimdi nasıl öğrenmek:

> [!div class="checklist"]
> - Görünümleri başlangıç kodundan ayırmak için uygulamakodunu yeniden düzenleme (adım 2-1)
> - Sayfa şablonu kullanarak görünüm oluşturma (adım 2-2)

## <a name="step-2-1-refactor-the-project-to-support-further-development"></a>Adım 2-1: Daha fazla geliştirmeyi desteklemek için projeyi yeniden düzenleme

"Boş Flask Web Project" şablonu tarafından oluşturulan kodda, tek bir görünümün yanında başlangıç kodu içeren tek bir *app.py* dosyanız vardır. Birden çok görünüme ve şablona sahip bir uygulamanın daha fazla geliştirilmesine izin vermek için, bu endişeleri ayırmak en iyisidir.

1. Proje `HelloFlask` klasörünüzde, adlı bir uygulama klasörü oluşturun **(Solution Explorer'da** projeyi sağ tıklatın ve Yeni**Klasör** **Ekle'yi** > seçin .)

2. *HelloFlask* klasöründe, `Flask` örneği oluşturan ve uygulamanın görünümlerini yükleyen (bir sonraki adımda oluşturulan) aşağıdaki içerikleri içeren * \_ \_init\_\_.py* adlı bir dosya oluşturun:

    ```python
    from flask import Flask
    app = Flask(__name__)

    import HelloFlask.views
    ```

3. *HelloFlask* klasöründe, aşağıdaki içerikleri içeren *views.py* adlı bir dosya oluşturun. init *views.py* `import HelloFlask.views` * \_ \_.py içinde kullandığınız için views.py adı önemlidir;\_\_* adlar eşleşmiyorsa çalışma zamanında bir hata görürsünüz.

    ```python
    from flask import Flask
    from HelloFlask import app

    @app.route('/')
    @app.route('/home')
    def home():
        return "Hello Flask!"
    ```

    İşlev ve rotayı yeniden `home`adlandırmanın yanı sıra, bu kod *app.py* `app` gelen sayfa oluşturma kodunu içerir ve * \_ \_init\_\_.py'de*bildirilen nesneyi içeri

4. *HelloFlask* adlı *şablonlar*bir alt klasör oluşturun , şimdilik boş kalır.

5. Projenin kök klasöründe, *app.py* *runserver.py*yeniden adlandırın ve içeriğin aşağıdaki kodla eşleşmesini sağlayabilir:

    ```python
    import os
    from HelloFlask import app    # Imports the code from HelloFlask/__init__.py

    if __name__ == '__main__':
        HOST = os.environ.get('SERVER_HOST', 'localhost')

        try:
            PORT = int(os.environ.get('SERVER_PORT', '5555'))
        except ValueError:
            PORT = 5555

        app.run(HOST, PORT)
    ```

6. Proje yapınız aşağıdaki görüntüye benzemeli:

    ![Kodu yeniden düzenlemeden sonra proje yapısı](media/flask/step02-project-structure.png)

7. **Hata** > **Ayıklama Hata Ayıklama** **(F5)** seçeneğini belirleyin veya uygulamayı başlatmak ve bir tarayıcı açmak için araç çubuğundaki **Web Sunucusu** düğmesini (gördüğünüz tarayıcı değişebilir) kullanın. Hem / ve / ev URL yolları deneyin.

8. Ayrıca kodun çeşitli bölümlerinde kesme noktaları ayarlayabilir ve başlangıç sırasını izlemek için uygulamayı yeniden başlatabilirsiniz. Örneğin, *runserver.py* ve *\_HelloFlask*init_*.py'nin*ilk satırlarına ve `return "Hello Flask!"` *views.py'daki*satırda bir kesme noktası ayarlayın. Sonra uygulamayı yeniden başlatın **(Hata** > **Ayıklama,** **Ctrl**+**F5**, veya araç çubuğu düğmesi aşağıda gösterilmiştir) ve **(F10)** kodu ile adım, ya da **F5**kullanarak her kesme noktasından çalıştırın .

    ![Visual Studio'da hata ayıklama araç çubuğundaki yeniden başlatma düğmesi](media/debugging-restart-toolbar-button.png)

9. Bitirdiğinizde uygulamayı durdurun.

### <a name="commit-to-source-control"></a>Kaynak denetimine bağlanma

Kodunuzda değişiklikler yaptığınız ve bunları başarıyla sınadığınız için, değişikliklerinizi gözden geçirmek ve kaynak denetimine işlemek için harika bir zaman. Bu öğreticideki sonraki adımlar, kaynak denetimine yeniden bağlanmanız için uygun zamanları hatırlatır ve sizi bu bölüme geri yönlendirir.

1. **Team Explorer'a**yönlendirilen Visual Studio'nun (aşağıda daire içine alınmış) altındaki değişiklikler düğmesini seçin.

    ![Visual Studio durum çubuğundaki kaynak denetimi değişiklikleri düğmesi](media/flask/step02-source-control-changes-button.png)

1. **Takım Gezgini'nde**, "Refactor kodu" gibi bir ileti girin ve **Tümünü İşley'i**seçin. Commit tamamlandığında, yerel olarak oluşturulan karma> bir ileti ** \<görürsünüz. Değişikliklerinizi sunucuyla paylaşmak için eşitleyin.** Değişiklikleri uzak deponuza itmek istiyorsanız, **Eşitle'yi**seçin ve **ardından Giden Taahhütler**altında **Itme'yi** seçin. Ayrıca, uzak bir zamana basmadan önce birden çok yerel taahhüt de biriktirebilirsiniz.

    ![Takım Gezgini'nde uzaklara itme taahhüdü](media/flask/step02-source-control-push-to-remote.png)

### <a name="question-how-frequently-should-one-commit-to-source-control"></a>Soru: Kaynak denetimine ne sıklıkta bağlanmak gerekir?

Cevap: Kaynak denetiminde değişiklik yapmak, değişiklik günlüğünde bir kayıt ve gerekirse depoyu geri döndürebileceğiniz bir nokta oluşturur. Her taahhüt, belirli değişiklikleri için de incelenebilir. Git'deki taahhütler ucuz olduğundan, sık sık taahhütlerde bulunmanın tek bir taahhütte daha fazla sayıda değişiklik biriktirmesinden daha iyidir. Açıkçası, her küçük değişikliği tek tek dosyalara işlemeniz gerekmez. Genellikle bir özellik eklerken, bu adımda yaptığınız gibi bir yapıyı değiştirirken veya bazı kod yeniden düzenlemesini yaparken işleme yaparsınız. Ayrıca, herkes için en iyi şekilde çalışan taahhütlerin parçalılığını takımınız için ekibinizdeki diğer kişilerle de kontrol edin.

Ne sıklıkta taahhüt ettiğiniz ve ne sıklıkta uzak bir depoya iterseniz iki farklı endişe vardır. Uzak depoya itmeden önce yerel deponuzda birden çok taahhüt biriktirebilirsiniz. Yine, ne sıklıkta taahhüt ettiğiniz, ekibinizin depoyu nasıl yönetmek istediğine bağlıdır.

## <a name="step-2-2-use-a-template-to-render-a-page"></a>Adım 2-2: Sayfayı işlemek için şablon kullanma

Şimdiye `home` kadar *views.py* sahip olduğunuz işlev, sayfa için düz metin HTTP yanıtından başka bir şey oluşturmaz. Ancak, çoğu gerçek dünya web sayfaları, genellikle canlı verileri içeren zengin HTML sayfaları ile yanıt. Gerçekten de, bir işlev kullanarak bir görünüm tanımlamak için birincil nedeni dinamik içerik oluşturmaktır.

Görünümün iade değeri yalnızca bir dize olduğundan, dinamik içeriği kullanarak bir dize içinde istediğiniz HTML'yi oluşturabilirsiniz. Ancak, işaretlemeyi verilerden ayırmak en iyisi olduğundan, biçimlendirmeyi bir şablona yerleştirmek ve verileri kodda tutmak çok daha iyidir.

1. Yeni başlayanlar için, bazı dinamik içeriğe sahip sayfa için satır altı HTML kullanan aşağıdaki kodu içerecek şekilde *views.py* edin:

    ```python
    from datetime import datetime
    from flask import render_template
    from HelloFlask import app

    @app.route('/')
    @app.route('/home')
    def home():
        now = datetime.now()
        formatted_now = now.strftime("%A, %d %B, %Y at %X")

        html_content = "<html><head><title>Hello Flask</title></head><body>"
        html_content += "<strong>Hello Flask!</strong> on " + formatted_now
        html_content += "</body></html>"

        return html_content
    ```

1. Uygulamayı çalıştırın ve tarih/saatin güncelleştirilip güncelleştirileni görmek için sayfayı birkaç kez yenileyin. Bitirdiğinizde uygulamayı durdurun.

1. Sayfa oluşturmayı şablon kullanacak şekilde dönüştürmek için, *index.html* *şablonlar* klasöründe aşağıdaki içeriğe sahip `{{ content }}` bir dosya oluşturun, burada kodda bir değer sağladığınız bir yer tutucu veya değiştirme jetonu *(şablon değişkeni*olarak da adlandırılır) bulunur:

    ```html
    <html>
        <head><title>Hello Flask</title></head>

        <body>
            {{ content }}
        </body>
    </html>
    ```

1. Şablonu `home` yüklemek `render_template` ve yer tutucunun adı ile eşleşen adlandırılmış bir bağımsız değişken kullanılarak yapılan "içerik" için bir değer sağlamak için işlevi değiştirin. Flask şablonlar klasöründe *şablonları* otomatik olarak arar, bu nedenle şablona giden yol bu klasöre göredir:

    ```python
    def home():
        now = datetime.now()
        formatted_now = now.strftime("%A, %d %B, %Y at %X")

        return render_template(
            "index.html",
            content = "<strong>Hello, Flask!</strong> on " + formatted_now)
    ```

1. Uygulamayı çalıştırın ve sayısal motor (Jinja) HTML `content` içeriğinden otomatik olarak kaçtıklarından, değerdeki satır içi HTML'nin HTML *olarak* işlemediğini gözlemleyin. Otomatik kaçış, enjeksiyon saldırılarına karşı kazara güvenlik açıklarını önler: geliştiriciler genellikle bir sayfadan giriş toplar ve şablon yer tutucu aracılığıyla başka bir sayfada değer olarak kullanır. Kaçmak, HTML'yi kodun dışında tutmanın yine en iyisi olduğunu da hatırlatıcı görevi görür.

    Buna göre, işaretleme içindeki her veri parçası için farklı yer tutucular içerecek şekilde *şablonları* gözden geçirin:

    ```html
    <html>
        <head>
            <title>{{ title }}</title>
        </head>
        <body>
            <strong>{{ message }}</strong>{{ content }}
        </body>
    </html>
    ```

    Ardından, `home` tüm yer tutucular için değerler sağlamak için işlevi güncelleştirin:

    ```python
    def home():
        now = datetime.now()
        formatted_now = now.strftime("%A, %d %B, %Y at %X")

        return render_template(
            "index.html",
            title = "Hello Flask",
            message = "Hello, Flask!",
            content = " on " + formatted_now)
    ```

1. Düzgün işlenmiş çıktıyı görmek için uygulamayı yeniden çalıştırın.

    ![Şablonu kullanarak uygulama çalıştırma](media/flask/step02-result.png)

1. Değişikliklerinizi kaynak denetimine bağla ve istenirse, [adım 2-1](#commit-to-source-control)altında açıklandığı gibi uzaktan deponuzu güncelleştirin.

### <a name="question-do-page-templates-have-to-be-in-a-separate-file"></a>Soru: Sayfa şablonları ayrı bir dosyada olmak zorunda mı?

Yanıt: Şablonlar genellikle ayrı HTML dosyalarında muhafaza edilebilse de, satır içinde şablon da kullanabilirsiniz. Ancak, biçimlendirme ve kod arasında temiz bir ayrım sağlamak için ayrı bir dosya kullanılması önerilir.

### <a name="question-must-templates-use-the-html-file-extension"></a>Soru: Şablonlar .html dosya uzantısını kullanmalı mı?

Cevap: Sayfa şablonu dosyalarının *.html* uzantısı tamamen isteğe bağlıdır, çünkü `render_template` her zaman işlevin ilk bağımsız değişkeninde dosyaya giden tam göreli yolu tanımlarsınız. Ancak, Visual Studio (ve diğer editörler) genellikle sayfa şablonları kesinlikle HTML olmadığı gerçeğini ağır basar *.html* dosyaları ile kod tamamlama ve sözdizimi renklendirme gibi özellikler verir.

Aslında, bir Flask projesiyle çalışırken Visual Studio, düzenlediğiniz HTML dosyasının aslında bir Flask şablonu olduğunu otomatik olarak algılar ve belirli otomatik tamamlama özellikleri sağlar. Örneğin, bir Flask sayfası şablonu yorum `{#`yazmaya başladığınızda, Visual `#}` Studio otomatik olarak kapanış karakterleri verir. **Yorum Seçimi** ve **Yorumsuz Seçim** komutları **(Gelişmiş'i** **Edit** > menüsünde ve araç çubuğunda) HTML yorumları yerine şablon açıklamaları da kullanır.

### <a name="question-can-templates-be-organized-into-further-subfolders"></a>Soru: Şablonlar başka alt klasörlere düzenlenebilir mi?

Cevap: Evet, alt klasörleri kullanabilir ve ardından çağırırda *şablonların* `render_template`altındaki göreli yola başvurabilirsiniz. Bunu yapmak, şablonlarınız için ad alanlarını etkili bir şekilde oluşturmanın harika bir yoludur.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Statik dosyalara hizmet, sayfa ekleme ve şablon kalıtımını kullanma](learn-flask-visual-studio-step-03-serve-static-files-add-pages.md)

## <a name="go-deeper"></a>Daha derine inin

- [Flask Quickstart - Oluşturma Şablonları](https://flask.palletsprojects.com/en/1.0.x/quickstart/#rendering-templates) (flask.pocoo.org)
- GitHub'da Öğretici kaynak kodu: [Microsoft/python-sample-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask)
