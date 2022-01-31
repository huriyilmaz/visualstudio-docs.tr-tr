---
title: 2. adım, görünümler Visual Studio şablonlarda Flask öğreticisini öğrenin
titleSuffix: ''
description: Özel olarak uygulama oluşturma ve görünümleri ve şablonları kullanma Visual Studio flask temel bilgilerine yönelik kılavuz.
ms.date: 01/26/2022
ms.topic: tutorial
author: rjmolyneaux
ms.author: rmolyneaux
manager: jmartens
ms.technology: vs-python
ms.workload:
- python
- data-science
ms.openlocfilehash: d678b3a306c515f0eb745360611bcbaad441af61
ms.sourcegitcommit: 20f9529648e69707063dccb2b15089bf4e9bf639
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/31/2022
ms.locfileid: "137887196"
---
# <a name="step-2-create-a-flask-app-with-views-and-page-templates"></a>2. Adım: Görünümler ve sayfa şablonlarıyla bir Flask uygulaması oluşturma

**Önceki adım: [Visual Studio proje ve çözüm oluşturma](learn-flask-visual-studio-step-01-project-solution.md)**

Bu öğreticinin 1. adımlarında tek sayfalı bir Flask uygulaması ve tek bir dosyada yer alan tüm kodlar yer almaktadır. Gelecekteki geliştirmelere izin vermek için en iyisi kodu yeniden düzenlemeniz ve sayfa şablonları için bir yapı oluşturmanızdır. Özellikle, uygulamanın görünümleri için kodu başlangıç kodu gibi diğer yönlerden ayırmak istiyorsanız.

Bu adımda şimdi şunların nasıl olduğunu öğreniriz:

> [!div class="checklist"]
> - Görünümleri başlangıç kodundan ayırmak için uygulama kodunu yeniden düzenleme (2-1. adım)
> - Sayfa şablonu kullanarak görünümü işleme (2-2. adım)

## <a name="step-2-1-refactor-the-project-to-support-further-development"></a>2-1. Adım: Daha fazla geliştirmeyi desteklemek için projeyi yeniden düzenleme

"Blank Flask Web Project" şablonu tarafından oluşturulan kodda, tek bir *görünümle birlikte başlangıç app.py* içeren tek bir app.py dosyanız vardır. Birden çok görünüme ve şablona sahip bir uygulamanın daha fazla geliştirilmesine olanak vermek için en iyisi bu endişeleri ayırmaktır.

1. Proje klasörünüzde adlı bir uygulama klasörü oluşturun `HelloFlask` (Çözüm Gezgini'da projeye sağ **tıklayın** ve **EkleYeni** >  **Klasör'e tıklayın**.)

2. *HelloFlask* klasöründe örneği *\_\_oluşturan ve uygulamanın görünümlerini yükleyen aşağıdaki içeriklerle init.py\_\_* `Flask` adlı bir dosya oluşturun (sonraki adımda oluşturulur):

    ```python
    from flask import Flask
    app = Flask(__name__)

    import HelloFlask.views
    ```

3. *HelloFlask klasöründe* aşağıdaki içeriklerle *views.py* adlı bir dosya oluşturun.  `import HelloFlask.views` *\_\_Init.py\_\_* views.py de kullanılan adlar önemli olduğundan, adlar eşleşmezse çalışma zamanında bir hatayla karşı karşınız olur.

    ```python
    from flask import Flask
    from HelloFlask import app

    @app.route('/')
    @app.route('/home')
    def home():
        return "Hello Flask!"
    ```

    İşlevi ve `home`yolu olarak yeniden eklemenin yanı sıra, bu kod *app.py* `app` sayfasından sayfa işleme kodunu içerir ve *init.py\_\_ içinde\_\_ bildirilen nesneyi içeri aktarıyor*.

4. *HelloFlask'ta templates* adlı bir *alt* klasör oluşturun ve bu klasör şimdilik boş kalır.

5. Projenin kök klasöründe, dosya adını app.py *runserver.py* ve  içeriğinin aşağıdaki kodla eşleşmesini sağlar:

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

6. Proje yapınız aşağıdaki görüntüye benzer şekilde görüntüye benzer:

    ![Project yeniden düzenleme sonrasında yapıyı yeniden düzenleme](media/flask/step02-project-structure.png)

7. Hata **Ayıklama Hata** >  **Ayıklamayı Başlat** (**F5**) öğesini seçin veya uygulamayı başlatmak ve bir tarayıcı açmak için araç **çubuğundaki Web Sunucusu** düğmesini (gördüğünüz tarayıcı farklılık gösterebilir) kullanın. / ve /home URL yollarını deneyin.

8. Ayrıca kodun çeşitli kısımlarında kesme noktaları ayarp başlatma sırasını takip etmek için uygulamayı yeniden başlatabilirsiniz. Örneğin, *runserver.py* ve *HelloFlask\_* init_ *.py'nin*`return "Hello Flask!"` ilk satırlarında ve *views.py.* Ardından uygulamayı yeniden başlatın (**DebugRestart** > , **CtrlShiftF5**++ veya aşağıda gösterilen araç çubuğu düğmesi) ve kodun üzerinden (**F10**) geçin veya **F5** kullanarak her kesme noktası üzerinden çalıştırın.

    ![Hata ayıklama araç çubuğundaki Yeniden Başlat düğmesi Visual Studio](media/debugging-restart-toolbar-button.png)

9. Bitirinca uygulamayı durdurun.

### <a name="commit-to-source-control"></a>Kaynak denetimine işleme

Kodunuz üzerinde değişiklikler yaptığınız ve bunları başarıyla test ettiyebilirsiniz. Şimdi değişikliklerinizi gözden geçirebilirsiniz ve kaynak denetimine işebilirsiniz. Bu öğreticinin sonraki adımlarında, kaynak denetimine yeniden işlemeniz için uygun zamanları anımsatır ve bu bölüme geri dönersiniz.

1. Uygulamanın (aşağıda daire içine Visual Studio) altındaki değişiklikler düğmesini seçin ve bu düğmeyi **Takım Gezgini.**

    ![Durum çubuğundaki kaynak denetimi Visual Studio düğmesi](media/flask/step02-source-control-changes-button.png)

1. Bu **Takım Gezgini** "Kodu yeniden düzenleme" gibi bir işleme iletisi girin ve Hepsini İşle'yi **seçin**. Yürütme tamamlandığında, Yerel olarak oluşturulmuş bir Commit **iletisiyle \<hash> karşılanır. Değişikliklerinizi sunucuyla paylaşmak için eşitle.** Değişiklikleri uzak depoya itmek için Eşitle'yi **ve** ardından Giden Commit'ler'in **altından** **Gönder'i seçin**. Uzak işlemeye itmeden önce birden çok yerel işleme de biriktirin.

    ![Uzak depolamada uzak işlemeleri Takım Gezgini](media/flask/step02-source-control-push-to-remote.png)

### <a name="question-how-frequently-should-one-commit-to-source-control"></a>Soru: Bir kaynak denetimi ne sıklıkta işlemeli?

Cevap: Değişiklikleri kaynak denetimine işlemek, değişiklik günlüğünde bir kayıt oluşturur ve gerekirse depoyu geri döndüren bir nokta oluşturur. Her işlemenin belirli değişiklikleri de incelendi. Git'te işlemeler uygun maliyetli olduğundan, tek bir işlemede çok sayıda değişiklik biriktirmek yerine sık işlemeler yapmak daha iyidir. Açıkça görülüyor ki her küçük değişikliği tek tek dosyalara işlemeye gerek yok. Genellikle bir özellik eklerken, bu adımda olduğu gibi bir yapıyı değiştirirken veya bazı kod yeniden düzenlemeleri yapılırken işleme yapılır. Ayrıca herkes için en iyi şekilde çalışacak işlemelerin ayrıntısı için takımınıza başkalarını da kontrol edin.

Ne sıklıkta işlemeniz ve uzak depoya işlemeleri ne sıklıkta ittmek iki farklı endişedir. Yerel depoda birden çok işlemeyi uzak depoya itmeden önce biriktirin. Yine işleme sıklık dereceniz, takımınız depoyu nasıl yönetmek istediğine bağlıdır.

## <a name="step-2-2-use-a-template-to-render-a-page"></a>2.-2. Adım: Sayfayı işlemek için şablon kullanma

Şu `home` ana kadar *views.py işlevi,* sayfa için düz metin HTTP yanıtından başka bir şey oluşturmaz. Ancak gerçek dünya web sayfalarının çoğu genellikle canlı verileri içeren zengin HTML sayfalarıyla yanıt verir. Aslında işlev kullanarak bir görünüm tanımlamanın birincil nedeni, içeriği dinamik olarak oluşturmaktır.

Görünümün dönüş değeri yalnızca bir dize olduğundan, dinamik içeriği kullanarak bir dize içinde, herhangi bir HTML oluşturabilirsiniz. Ancak, işaretlemeyi verilerden ayırmanın en iyisi olduğundan, işaretlemeyi bir şablona yer ve verileri kodda tutmak çok daha iyidir.

1. Başlangıç olarak, *sayfa views.py* satır içi HTML kullanan aşağıdaki kodu içermesi için sayfayı düzenleyin ve bazı dinamik içerikler ekleyin:

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

1. Tarihin/saatin güncelleştirilmiş olduğunu görmek için uygulamayı çalıştırın ve sayfayı birkaç kez yenileyin. Bitirinca uygulamayı durdurun.

1. Sayfa işlemeyi şablon kullanmak üzere dönüştürmek için, *templates* klasöründe aşağıdaki içeriğe sahipindex.htmladlı bir dosya oluşturun. Burada, `{{ content }}` kodda bir değer temin etmek için bir yer tutucu veya değiştirme belirteci (şablon değişkeni olarak da ** *denir) bulunur*:

    ```html
    <html>
        <head><title>Hello Flask</title></head>

        <body>
            {{ content }}
        </body>
    </html>
    ```

1. Şablonu yüklemek `home` ve yer tutucu `render_template` adıyla eşleşen adlandırılmış bir bağımsız değişken kullanılarak yapılan "content" için bir değer sağlamak için işlevini kullanmak üzere değiştirme. Flask şablonlar klasöründe şablonları otomatik *olarak* aramaz, bu nedenle şablonun yolu bu klasöre göredir:

    ```python
    def home():
        now = datetime.now()
        formatted_now = now.strftime("%A, %d %B, %Y at %X")

        return render_template(
            "index.html",
            content = "<strong>Hello, Flask!</strong> on " + formatted_now)
    ```

1. Sonuçları görmek için uygulamayı çalıştırın ve templating engine (Jinja) html içeriğine otomatik olarak kaçışı olduğundan değer içinde satır *içi HTML'nin* `content` HTML olarak işlenmez. Otomatik kaçış, ekleme saldırılarında yanlışlıkla güvenlik açıklarını önler: Geliştiriciler genellikle bir sayfadan giriş toplar ve şablon yer tutucusu aracılığıyla bunu başka bir sayfada değer olarak kullanır. Kaçış, HTML kodunun dışında tutmanın yeniden en iyi olduğunu anımsatıcı olarak da görev sağlar.

    Buna uygun olarak, *templates\index.html* biçimlendirme içindeki her veri parçası için ayrı yer tutucular içermesi için aşağıdaki bilgileri gözden geçirebilirsiniz:

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

    Ardından işlevi tüm `home` yer tutuculara değer sağlayacak şekilde güncelleştirin:

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

1. Düzgün işlenmiş çıkışı görmek için uygulamayı yeniden çalıştırın.

    ![Şablon kullanarak uygulama çalıştırma](media/flask/step02-result.png)

1. İsterseniz, 2-1. adım altında açıklandığı gibi değişikliklerinizi kaynak denetimine işin ve uzak [depoyu güncelleştirin](#commit-to-source-control).

### <a name="question-do-page-templates-have-to-be-in-a-separate-file"></a>Soru: Sayfa şablonlarının ayrı bir dosyada olması gerekir mi?

Cevap: Şablonlar genellikle ayrı HTML dosyalarında korunsa da satır içi şablon da kullanabilirsiniz. Ancak işaretleme ile kod arasında temiz bir ayrım yapmak için ayrı bir dosya kullanılması önerilir.

### <a name="question-must-templates-use-the-html-file-extension"></a>Soru: Şablonlar dosya uzantısını .html mı?

Cevap: *.html* dosyanın göreli yolunu işlevin ilk bağımsız değişkende her zaman tam olarak tanımlaysınız, sayfa şablonu dosyaları için uzantı tamamen isteğe `render_template` bağlıdır. Ancak Visual Studio (ve diğer düzenleyiciler) genellikle.htmldosyalarıyla kod tamamlama ve söz dizimi renklendirmesi gibi özellikler sunar ** ve bu da sayfa şablonlarının tamamen HTML olmadığını gösterir.

Aslında, bir Flask projesiyle çalışırken, Visual Studio html dosyası aslında bir Flask şablonu olduğunda otomatik olarak algılar ve belirli otomatik tamamlama özellikleri sağlar. Örneğin, bir Flask sayfa şablonu açıklaması yazmaya başladığınızda, `{#`Visual Studio otomatik olarak kapatma karakterleri `#}` verir. Açıklama **Seçimi ve** **Açıklama Seçimini Kaldır** komutları (**EditAdvanced**  >  menüsünde ve araç çubuğunda) HTML açıklamalarının yerine şablon açıklamalarını da kullanır.

### <a name="question-can-templates-be-organized-into-further-subfolders"></a>Soru: Şablonlar daha fazla alt klasöre düzenleniyor mu?

Cevap: Evet, alt klasörleri kullanabilir ve ardından çağrısında şablonlar altındaki *göreli yola* başvurabilirsiniz `render_template`. Bunu yapmak, şablonlarınız için etkili bir şekilde ad alanları oluşturmanın harika bir yoludur.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Statik dosyaları hizmet etme, sayfa ekleme ve şablon devralma kullanma](learn-flask-visual-studio-step-03-serve-static-files-add-pages.md)

## <a name="go-deeper"></a>Daha derine gitme

- [Flask Hızlı Başlangıç - İşleme Şablonları](https://flask.palletsprojects.com/en/1.0.x/quickstart/#rendering-templates) (flask.pocoo.org)
- GitHub öğreticisi: [Microsoft/python-sample-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask)
