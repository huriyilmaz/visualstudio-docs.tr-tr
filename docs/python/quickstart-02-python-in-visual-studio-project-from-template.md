---
title: Hızlı başlangıç-şablon kullanarak bir Python projesi oluşturma
description: bu hızlı başlangıçta, temel bir flask uygulaması için yerleşik şablonu kullanarak Python için bir Visual Studio projesi oluşturacaksınız.
ms.date: 12/06/2018
ms.topic: quickstart
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: c77f8c52e62772cbef61f7ae07f29a2594e608c0
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726790"
---
# <a name="quickstart-create-a-python-project-from-a-template-in-visual-studio"></a>Hızlı başlangıç: Visual Studio bir şablondan Python projesi oluşturma

[Visual Studio ' de Python desteğini](installing-python-support-in-visual-studio.md)yükledikten sonra, çeşitli şablonlar kullanarak yeni bir Python projesi oluşturmak kolaydır. Bu hızlı başlangıçta, şablon kullanarak basit bir Flask uygulaması oluşturacaksınız. Elde edilen proje, hızlı başlangıç aracılığıyla oluşturduğunuz projeye benzer. [Flask ile bir Web uygulaması oluşturun](../ide/quickstart-python.md).

1. Visual Studio’yu çalıştırın.

1. üst menü çubuğundan **dosya**  >  **yeni**  >  **Project**' yi seçin, sonra **yeni Project** iletişim kutusunda "boş flask" araması yapın, ortadaki listeden **boş flask Web Project** şablonunu seçin, projeye bir ad verin ve **tamam**' ı seçin:

    ![boş flask Web Project şablonuyla yeni bir proje oluşturma](media/quickstart-python-06-blank-flask-template.png)

1. Visual Studio, **bu projenin dış paket gerektirdiğini** belirten bir iletişim kutusu ister. Bu iletişim kutusu, şablon Flask üzerinde bir bağımlılık belirten bir *requirements.txt* dosyası içerdiğinden görüntülenir. Visual Studio paketleri otomatik olarak yükleyebilir ve bunları bir *sanal ortama* yüklemek için seçenek sunar. Bir sanal ortamın kullanılması için genel bir ortama yükleme yapılması önerilir, bu nedenle devam etmek için **sanal ortama yükleme** ' yi seçin.

    ![Sanal ortama Flask yükleme](media/quickstart-python-07-install-into-virtual-environment.png)

1. Visual Studio **sanal ortam ekle** iletişim kutusunu görüntüler. Varsayılanı kabul edin ve **Oluştur**' u ve ardından herhangi bir yükseltme isteğinde onay ' yı seçin.

    > [!Tip]
    > bir projeye başladığınızda, çoğu Visual Studio şablon sizi davet etmek için hemen bir sanal ortam oluşturmanız önerilir. Sanal ortamlar, kitaplıkları eklerken ve kaldırırken projenizin tam gereksinimlerini zaman içinde tutar. Daha sonra bu bağımlılıkları diğer geliştirme bilgisayarlarına (kaynak denetimi kullanılırken olduğu gibi) yeniden yüklemek için kullandığınız ve projeyi bir üretim sunucusuna dağıttığınızda kolayca *requirements.txt* bir dosya oluşturabilirsiniz. Sanal ortamlar ve avantajları hakkında daha fazla bilgi için bkz. [sanal ortamları kullanma](../python/selecting-a-python-environment-for-a-project.md#use-virtual-environments) ve [gerekli paketleri requirements.txtile yönetme ](../python/managing-required-packages-with-requirements-txt.md).

1. Visual Studio bu ortamı oluşturduktan sonra, *requirements.txt* birlikte bir *app.py* dosyasına sahip olup olmadığını görmek için **Çözüm Gezgini** bakın. Şablonda, daha fazla eklenen bölümle bir [Flask ile bir Web uygulaması oluşturmak](../ide/quickstart-python.md)için *app.py* açın. Aşağıda gösterilen tüm kod şablon tarafından oluşturulur, bu nedenle *app.py* 'e dilediğiniz şekilde yapıştırmanız gerekmez.

    Kod, gerekli içeri aktarımlarla başlar:

    ```python
    from flask import Flask
    app = Flask(__name__)
    ```

    Sonraki bir, bir uygulamayı bir Web konağına dağıtmada yararlı olabilecek aşağıdaki satırdır:

    ```python
    wsgi_app = app.wsgi_app
    ```

    Ardından, bir görünümü tanımlayan basit bir işlevde yol dekoratörü gelir:

    ```python
    @app.route('/')
    def hello():
        """Renders a sample page."""
        return "Hello World!"
    ```

    Son olarak, aşağıdaki başlangıç kodu, Konağı ve bağlantı noktasını sabit kodlamak yerine ortam değişkenleri aracılığıyla ayarlamanıza olanak sağlar. Bu kod, kodu değiştirmeden hem geliştirme hem de üretim makinelerinde yapılandırmayı kolayca denetlemenize olanak tanır:

    ```python
    if __name__ == '__main__':
        import os
        HOST = os.environ.get('SERVER_HOST', 'localhost')
        try:
            PORT = int(os.environ.get('SERVER_PORT', '5555'))
        except ValueError:
            PORT = 5555
        app.run(HOST, PORT)
    ```

1.   >  Uygulamayı çalıştırmak ve ' de bir tarayıcı açmak için **hata ayıklama olmadan Başlat** ' ı seçin `localhost:5555` .

**soru: diğer Python şablonları Visual Studio teklif veriyor?**

**cevap**: python iş yükü yüklüyken, Visual Studio [flask, şişe ve docgo web çerçeveleri](../python/python-web-application-project-templates.md), Azure bulut hizmetleri, farklı makine öğrenimi senaryoları ve hatta bir Python uygulaması içeren var olan bir klasör yapısından proje oluşturmak için bir şablon dahil çeşitli proje şablonları sağlar. bunlara   >    >  , **Python** dil düğümünü ve onun alt düğümlerini seçerek dosya yeni **Project** iletişim kutusu üzerinden erişirsiniz.

Visual Studio ayrıca, bir python sınıfı, bir python paketi, bir python birimi testi, *web.config* dosyaları ve daha fazlasını oluşturmak için çeşitli dosya veya *öğe şablonları* sağlar. açık bir Python projeniz olduğunda, **Project**  >  **yeni öğe ekle** menü komutu aracılığıyla öğe şablonlarına erişirsiniz. [Öğe şablonları](python-item-templates.md) başvurusuna bakın.

Şablonları kullanmak, bir projeyi başlatırken veya dosya oluştururken önemli bir zaman kazandırabilir ve ayrıca farklı uygulama türleri ve kod yapıları hakkında bilgi edinmek için harika bir yoldur. Çeşitli şablonlardan proje ve öğelerin oluşturulması, neleri sundukları hakkında bilgi edinmek için birkaç dakika sürer.

**Soru: Cookiecutter şablonlarını da kullanabilir miyim?**

**Cevap**: Evet! aslında Visual Studio, [hızlı başlangıç: bir Cookiecutter şablonundan proje oluşturma](../python/quickstart-04-python-in-visual-studio-project-from-cookiecutter.md)hakkında bilgi edinmek için doğrudan Cookiecutter ile tümleştirme sağlar.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Öğretici: Visual Studio 'de Python ile çalışma](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Mevcut bir Python yorumlayıcısını el ile tanımla](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
- [Visual Studio 2015 ve önceki sürümlerde Python desteği yüklemesi](installing-python-support-in-visual-studio.md)
- [Konum yüklemeleri](installing-python-support-in-visual-studio.md#install-locations)
