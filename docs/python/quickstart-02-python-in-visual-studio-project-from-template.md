---
title: Hızlı Başlangıç - Şablon kullanarak Python projesi oluşturma
description: Bu hızlı başlangıçta, temel bir Flask Visual Studio yerleşik şablonunu kullanarak Python için bir Visual Studio projesi oluşturuluyor.
ms.date: 12/06/2018
ms.topic: quickstart
author: rjmolyneaux
ms.author: rmolyneaux
manager: jmartens
ms.technology: vs-python
ms.workload:
- python
- data-science
ms.openlocfilehash: 4e8b605a66b4b7c7e16873d84efb150abfa6620d
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129971341"
---
# <a name="quickstart-create-a-python-project-from-a-template-in-visual-studio"></a>Hızlı Başlangıç: Visual Studio'da şablondan Python Visual Studio

Visual Studio'da [Python desteğini](installing-python-support-in-visual-studio.md)yüklediniz, çeşitli şablonlar kullanarak yeni bir Python projesi oluşturmak kolaydır. Bu Hızlı Başlangıçta şablon kullanarak basit bir Flask uygulaması oluşturabilirsiniz. Sonuçta elde edilen proje, Hızlı Başlangıç [- Flask](../ide/quickstart-python.md)ile web uygulaması oluşturma aracılığıyla el ile oluşturmalısınız.

1. Visual Studio’yu çalıştırın.

1. Üst menü çubuğundan Dosya Yeni Project'yi seçin, ardından Yeni Project iletişim kutusunda  >    >  "boş **flask"** araması yazın,  ortadaki listede Boş Flask Web Project şablonunu seçin, projeye bir ad girin ve Tamam'ı **seçin:**

    ![Boş Flask Web Uygulaması şablonuyla yeni Project oluşturma](media/quickstart-python-06-blank-flask-template.png)

1. Visual Studio, Bu proje dış paketler gerektiriyor ifadesini içeren **bir iletişim kutusu girmenizi sağlar.** Şablon Flask bağımlılığını *belirten birrequirements.txt* dosyası içerir. Visual Studio paketleri otomatik olarak yükleyebilir ve bunları sanal bir ortama yükleme *seçeneği sunar.* Genel bir ortama yükleme yerine sanal ortam kullanılması önerilir, bu nedenle devam etmek **için Sanal ortama yükle'yi** seçin.

    ![Flask'i sanal ortama yükleme](media/quickstart-python-07-install-into-virtual-environment.png)

1. Visual Studio Ortam Ekle **iletişim kutusunu** görüntüler. Varsayılanı kabul et ve **Oluştur'un** ardından tüm yükseltme isteklerini onayla'ya seçin.

    > [!Tip]
    > Bir projeye başlarken, çoğu şablon sizi davet Visual Studio hemen sanal ortam oluşturmanız önerilir. Sanal ortamlar, siz kitaplıkları eklerken ve kaldırırken projenizin zaman içinde tam gereksinimlerini karşılar. Daha sonra kolayca bir *requirements.txt* dosyası oluşturabilirsiniz. Bu dosya, bu bağımlılıkları diğer geliştirme bilgisayarlarına (kaynak denetimi kullanırken olduğu gibi) ve projeyi bir üretim sunucusuna dağıtırken yeniden yükleyebilirsiniz. Sanal ortamlar ve bunların avantajları hakkında daha fazla bilgi için [bkz. Sanal ortamları kullanma](../python/selecting-a-python-environment-for-a-project.md#use-virtual-environments) ve Sanal ortamlarla [gerekli requirements.txt. ](../python/managing-required-packages-with-requirements-txt.md)

1. Bu Visual Studio ortamını oluşturduğunda,  Çözüm Gezgini ile birlikte bir app.py *dosyanız* olduğunu görmek için *requirements.txt.* Şablonun *app.py* hızlı başlangıç [- Flask](../ide/quickstart-python.md)ile bir web uygulaması oluşturma içinde birkaç bölüm eklenmiştir. Aşağıda gösterilen kodun hepsi şablon tarafından oluşturulmuştur, bu nedenle herhangi bir kodu kendi kendinize *app.py* gerek yok.

    Kod gerekli içeri aktarmalarla başlar:

    ```python
    from flask import Flask
    app = Flask(__name__)
    ```

    Sonraki satır, bir web ana bilgisayar için uygulama dağıtırken yararlı olabilir:

    ```python
    wsgi_app = app.wsgi_app
    ```

    Ardından görünüm tanımlayan basit bir işlevde yol dekoratörü gelir:

    ```python
    @app.route('/')
    def hello():
        """Renders a sample page."""
        return "Hello World!"
    ```

    Son olarak, aşağıdaki başlangıç kodu, konak ve bağlantı noktasını sabit kodlamak yerine ortam değişkenleri aracılığıyla ayarlamaya olanak sağlar. Bu tür kod, kodu değiştirmeden hem geliştirme hem de üretim makinelerinin yapılandırmasını kolayca denetlemenizi sağlar:

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

1. Hata **Ayıklama Olmadan**  >  **Başlat'ı seçerek** uygulamayı çalıştırın ve bir tarayıcı `localhost:5555` açın.

**Soru: Diğer Python şablonları Visual Studio sunuyor?**

**Cevap:** Python iş yükü yüklendikten sonra Visual Studio [Flask, Bottle ve Django web çerçeveleri,](../python/python-web-application-project-templates.md)Azure bulut hizmetleri, farklı makine öğrenmesi senaryoları ve hatta Python uygulaması içeren mevcut bir klasör yapısından proje oluşturmak için bir şablon gibi çeşitli proje şablonları sağlar. Bunlara, Python dil **düğümünü** ve Project düğümlerini seçerek Dosya Yeni Dosya  >    >   iletişim kutusu aracılığıyla erişebilirsiniz. 

Visual Studio Python sınıfını, Python paketini,  Python birim testini, veri dosyalarını ve daha fazlasını hızlı bir şekilde oluşturmak için çeşitli *dosya veyaweb.config* şablonları da sağlar. Bir Python projeniz açık olduğunda öğe şablonlarına Yeni Öğe Ekle Project  >  **komutuyla erişebilirsiniz.** Öğe [şablonları başvurusuna](python-item-templates.md) bakın.

Şablonları kullanmak, bir projeyi başlatma veya dosya oluşturma konusunda önemli zaman tasarrufu sağlar ve ayrıca farklı uygulama türleri ve kod yapıları hakkında bilgi edinmek için harika bir yol sağlar. Çeşitli şablonlardan proje ve öğe oluşturmak birkaç dakikanızı alır ve bu şablonların neler sun olduklarını tanımanız faydalı olur.

**Soru: Cookiecutter şablonlarını da kullanabilir miyim?**

**Cevap:** Evet! Aslında, Visual Studio Cookiecutter ile doğrudan tümleştirme sağlar. Bu tümleştirmeyi Hızlı [Başlangıç: Cookiecutter](../python/quickstart-04-python-in-visual-studio-project-from-cookiecutter.md)şablonundan proje oluşturma aracılığıyla öğrenebilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Öğretici: Python ile Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Mevcut Python yorumlayıcıyı el ile tanımlama](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
- [Visual Studio 2015 ve önceki sürümlerde Python desteğini yükleme](installing-python-support-in-visual-studio.md)
- [Yükleme konumları](installing-python-support-in-visual-studio.md#install-locations)
