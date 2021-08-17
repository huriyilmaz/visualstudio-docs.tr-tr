---
title: 2. adım, görünümler Visual Studio şablonlarda Flask öğreticisini öğrenin
titleSuffix: ''
description: Özel olarak uygulama oluşturma ve görünümleri ve şablonları kullanma Visual Studio flask temel bilgilerine yönelik kılavuz.
ms.date: 01/07/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 82c15d8da2aa2deebb3150c984bf77ca8b9dc4ec00891313e0b6841d04f75394
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121395830"
---
# <a name="step-2-create-a-flask-app-with-views-and-page-templates"></a>2. Adım: Görünümler ve sayfa şablonlarıyla bir Flask uygulaması oluşturma

**Önceki adım: [Visual Studio proje ve çözüm oluşturma](learn-flask-visual-studio-step-01-project-solution.md)**

Bu öğreticinin 1. adımlarında tek sayfalı bir Flask uygulaması ve tek bir dosyada yer alan tüm kodlar yer almaktadır. Gelecekteki geliştirmelere izin vermek için en iyisi kodu yeniden düzenlemeniz ve sayfa şablonları için bir yapı oluşturmanızdır. Özellikle, uygulamanın görünümleri için kodu başlangıç kodu gibi diğer yönlerden ayırmak istiyorsanız.

Bu adımda şimdi şunların nasıl olduğunu öğreniriz:

> [!div class="checklist"]
> - Görünümleri başlangıç kodundan ayırmak için uygulama kodunu yeniden düzenleme (2-1. adım)
> - Sayfa şablonu kullanarak görünümü işleme (2-2. adım)

## <a name="step-2-1-refactor-the-project-to-support-further-development"></a>2-1. Adım: Daha fazla geliştirmeyi desteklemek için projeyi yeniden düzenleme

"Blank Flask Web Project" şablonu tarafından oluşturulan kodda, tek bir *görünümle* birlikte başlangıç app.py içeren tek bir app.py dosyanız vardır. Birden çok görünüme ve şablona sahip bir uygulamanın daha fazla geliştirilmesine olanak vermek için en iyisi bu endişeleri ayırmaktır.

1. Proje klasörünüzde adlı bir uygulama klasörü oluşturun (Çözüm Gezgini'de projeye sağ tıklayın ve Yeni Klasör `HelloFlask`    >  **Ekle'yi seçin.)**

2. *HelloFlask* klasöründe örneği oluşturan ve uygulamanın görünümlerini yükleyen aşağıdaki içeriklerle *\_ \_ init \_ \_ .py* adlı bir dosya oluşturun (sonraki adımda `Flask` oluşturulur):

    ```python
    from flask import Flask
    app = Flask(__name__)

    import HelloFlask.views
    ```

3. *HelloFlask klasöründe* aşağıdaki içeriklerle *views.py* adlı bir dosya oluşturun. Init  `import HelloFlask.views` *\_ \_ \_ \_ .py views.py de* kullanılan adlar önemli olduğundan, adlar eşleşmezse çalışma zamanında bir hata alırsınız.

    ```python
    from flask import Flask
    from HelloFlask import app

    @app.route('/')
    @app.route('/home')
    def home():
        return "Hello Flask!"
    ```

    İşlevi ve yolu olarak yeniden eklemenin yanı sıra, bu kod app.py'den sayfa işleme kodunu içerir ve init .py içinde bildirilen nesneyi `home`  `app` içeri *\_ \_ \_ \_ aktarıyor.*

4. *HelloFlask'ta templates* adlı bir *alt* klasör oluşturun ve bu klasör şimdilik boş kalır.

5. Projenin kök klasöründe, dosya  adını app.py *runserver.py* olarak yeniden adlandırarak içeriğinin aşağıdaki kodla eşleşmesini sağlar:

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

7. Hata **AyıklamaYı**  >  **Başlat** (**F5**) öğesini seçin veya uygulamayı başlatmak ve bir tarayıcı açmak için araç **çubuğundaki Web Sunucusu** düğmesini (gördüğünüz tarayıcı farklılık gösterebilir) kullanın. / ve /home URL yollarını deneyin.

8. Ayrıca kodun çeşitli kısımlarında kesme noktaları ayarp başlatma sırasını takip etmek için uygulamayı yeniden başlatabilirsiniz. Örneğin, runserver.py ve *\_ HelloFlask'ın* *ilk* satırlarında *.py* init_ bir kesme noktası ayarlayın ve `return "Hello Flask!"` views.py.  Ardından uygulamayı **yeniden** başlatın ( Yeniden Başlat ,  >   **Ctrl** + **Shift** + **F5** veya aşağıda gösterilen araç çubuğu düğmesi) ve kodun üzerinden (**F10**) geçin veya F5 kullanarak her kesme noktası üzerinden çalıştırın.

    ![Hata ayıklama araç çubuğundaki Yeniden Başlat düğmesi Visual Studio](media/debugging-restart-toolbar-button.png)

9. Bitirin ve uygulamayı durdurun.

### <a name="commit-to-source-control"></a>Kaynak denetimine işleme

Kodunuz üzerinde değişiklikler yaptığınız ve bunları başarıyla test ettiysiniz, şimdi değişikliklerinizi gözden geçirmek ve kaynak denetimine işlemek için harika bir zamandır. Bu öğreticinin sonraki adımlarında, kaynak denetimine yeniden işlemeniz için uygun zamanları anımsatır ve bu bölüme geri dönersiniz.

1. Uygulamanın (aşağıda daire içine Visual Studio) altındaki değişiklikler düğmesini seçin ve bu düğmeyi **Takım Gezgini.**

    ![Durum çubuğundaki kaynak denetimi Visual Studio düğmesi](media/flask/step02-source-control-changes-button.png)

1. Bu **Takım Gezgini**, "Kodu yeniden düzenleme" gibi bir işleme iletisi girin ve Hepsini **İşle'yi seçin.** Yürütme tamamlandığında, Yerel olarak oluşturulmuş bir Commit **\<hash> iletisiyle karşılanır. Değişikliklerinizi sunucuyla paylaşmak için eşitle.** Değişiklikleri uzak depoya itmek için Eşitle'yi ve **ardından** Giden Commit'ler altında **Gönder'i seçin.**  Uzak işlemeye itmeden önce birden çok yerel işleme de biriktirin.

    ![Uzak depolamada uzak işlemeleri Takım Gezgini](media/flask/step02-source-control-push-to-remote.png)

### <a name="question-how-frequently-should-one-commit-to-source-control"></a>Soru: Bir kaynak denetimi ne sıklıkta işlemeli?

Cevap: Değişiklikleri kaynak denetimine işlemek, değişiklik günlüğünde bir kayıt oluşturur ve gerekirse depoyu geri döndüren bir nokta oluşturur. Her işlemenin belirli değişiklikleri de incelendi. Git'te işlemeler uygun maliyetli olduğundan, tek bir işlemede çok sayıda değişiklik biriktirmek yerine sık işlemeler yapmak daha iyidir. Açıkça görülüyor ki her küçük değişikliği tek tek dosyalara işlemeye gerek yok. Genellikle bir özellik eklerken, bu adımda olduğu gibi bir yapıyı değiştirirken veya bazı kod yeniden düzenlemeleri yapılırken işleme yapılır. Ayrıca herkes için en uygun işlemelerin ayrıntısı için takımınıza başkalarını da kontrol edin.

Ne sıklıkta işlemeniz ve uzak bir depoya işlemeleri ne sıklıkta ittmeniz iki farklı endişedir. Yerel depoda birden çok işlemeyi uzak depoya itmeden önce birikmeye devam ediyor olabilir. Yine işleme sıklık dereceniz, takımınız depoyu nasıl yönetmek istediğine bağlıdır.

## <a name="step-2-2-use-a-template-to-render-a-page"></a>2.-2. Adım: Sayfayı işlemek için şablon kullanma

Şu ana kadar içinde sahip views.py, sayfa için düz metin `home` HTTP yanıtından başka bir şey oluşturmaz.  Ancak gerçek dünya web sayfalarının çoğu genellikle canlı verileri içeren zengin HTML sayfalarıyla yanıt verir. Aslında işlev kullanarak bir görünüm tanımlamanın birincil nedeni içeriği dinamik olarak oluşturmaktır.

Görünümün dönüş değeri yalnızca bir dize olduğundan, dinamik içeriği kullanarak bir dize içinde, herhangi bir HTML oluşturabilirsiniz. Ancak, en iyisi işaretlemeyi verilerden ayırmak olduğundan, işaretlemeyi bir şablona yer ve verileri kodda tutmak çok daha iyidir.

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

1. Tarihin/saatin güncelleştirilmiş olduğunu görmek için uygulamayı çalıştırın ve sayfayı birkaç kez yenileyin. Bitirin ve uygulamayı durdurun.

1. Sayfa işlemeyi şablon kullanmak üzere dönüştürmek için, *templates* klasöründe aşağıdaki içeriğe sahip *index.html* adlı bir dosya oluşturun. Burada, kodda bir değer sağlarsınız yer tutucu veya değiştirme belirteci (şablon değişkeni olarak da `{{ content }}` denir) bulunur: 

    ```html
    <html>
        <head><title>Hello Flask</title></head>

        <body>
            {{ content }}
        </body>
    </html>
    ```

1. Şablonu yüklemek ve yer tutucu adıyla eşleşen adlandırılmış bir bağımsız değişken kullanılarak yapılan "content" için bir değer sağlamak için `home` `render_template` işlevini kullanmak üzere değiştirme. Flask şablonlar klasöründe şablonları otomatik *olarak* aramaz, bu nedenle şablonun yolu bu klasöre göredir:

    ```python
    def home():
        now = datetime.now()
        formatted_now = now.strftime("%A, %d %B, %Y at %X")

        return render_template(
            "index.html",
            content = "<strong>Hello, Flask!</strong> on " + formatted_now)
    ```

1. Sonuçları görmek için uygulamayı çalıştırın ve `content` templating engine (Jinja)  html içeriğine otomatik olarak kaçışı olduğundan değer içinde satır içi HTML'nin HTML olarak işlenmez. Otomatik kaçış, ekleme saldırılarında yanlışlıkla güvenlik açıklarını önler: Geliştiriciler genellikle bir sayfadan giriş toplar ve şablon yer tutucusu aracılığıyla bunu başka bir sayfada değer olarak kullanır. Kaçış ayrıca HTML kodunun dışında tutmanın en iyisi olduğunu anımsatıcı olarak da görevdir.

    Buna uygun olarak, *templates\index.htmiçindeki* her veri parçası için ayrı yer tutucular içermesi için l'yi gözden geçirebilirsiniz:

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

    Ardından işlevi `home` tüm yer tutuculara değer sağlayacak şekilde güncelleştirin:

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

1. İsterseniz, [2-1.](#commit-to-source-control)adım altında açıklandığı gibi kaynak denetimine değişikliklerinizi işin ve uzak depoyu güncelleştirin.

### <a name="question-do-page-templates-have-to-be-in-a-separate-file"></a>Soru: Sayfa şablonlarının ayrı bir dosyada olması gerekir mi?

Cevap: Şablonlar genellikle ayrı HTML dosyalarında korunsa da satır içi şablon da kullanabilirsiniz. Ancak işaretleme ile kod arasında temiz bir ayrım yapmak için ayrı bir dosya kullanılması önerilir.

### <a name="question-must-templates-use-the-html-file-extension"></a>Soru: Şablonlar dosya uzantısını .html mı?

Cevap: *.html* dosyanın göreli yolunu işlevin ilk bağımsız değişkende her zaman tam olarak tanımlaysınız, sayfa şablonu dosyaları için uzantı tamamen `render_template` isteğe bağlıdır. Ancak Visual Studio (ve diğer düzenleyiciler) genellikle.htmldosyalarıyla kod tamamlama  ve söz dizimi renklendirmesi gibi özellikler sağlar ve bu da sayfa şablonlarının tamamen HTML olmadığının ağır basıyor olmasıdır.

Aslında, bir Flask projesiyle çalışırken, Visual Studio html dosyasının aslında bir Flask şablonu olduğunu otomatik olarak algılar ve belirli otomatik tamamlama özellikleri sağlar. Örneğin, bir Flask sayfa şablonu açıklaması yazmaya `{#` başladığınızda, Visual Studio otomatik olarak kapatma karakterlerini `#}` verir. Açıklama **Seçimi ve** **Açıklama Seçimini Kaldır komutları** (Gelişmiş Düzenle menüsünde ve araç çubuğunda) HTML açıklamalarının yerine şablon   >   açıklamalarını da kullanır.

### <a name="question-can-templates-be-organized-into-further-subfolders"></a>Soru: Şablonlar daha fazla alt klasöre düzenleniyor mu?

Cevap: Evet, alt klasörleri kullanabilir ve ardından çağrısında şablonlar altındaki *göreli yola* `render_template` başvurabilirsiniz. Bunu yapmak, şablonlarınız için etkili bir şekilde ad alanları oluşturmanın harika bir yoludur.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Statik dosyaları hizmet etme, sayfa ekleme ve şablon devralma kullanma](learn-flask-visual-studio-step-03-serve-static-files-add-pages.md)

## <a name="go-deeper"></a>Daha derine gitme

- [Flask Hızlı Başlangıç - İşleme Şablonları](https://flask.palletsprojects.com/en/1.0.x/quickstart/#rendering-templates) (flask.pocoo.org)
- GitHub öğreticisi: [Microsoft/python-sample-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask)
