---
title: Quickstart - Şablon kullanarak Python projesi oluşturma
description: Bu hızlı başlangıçta, temel bir Flask uygulaması için yerleşik şablonu kullanarak Python için bir Visual Studio projesi oluşturursunuz.
ms.date: 12/06/2018
ms.topic: quickstart
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 089be3e6f28a939979f6bd97097ea7558824b493
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "62429775"
---
# <a name="quickstart-create-a-python-project-from-a-template-in-visual-studio"></a>Hızlı başlangıç: Visual Studio'daki şablondan Python projesi oluşturma

[Visual Studio'ya Python desteğini yükledikten](installing-python-support-in-visual-studio.md)sonra, çeşitli şablonlar kullanarak yeni bir Python projesi oluşturmak kolaydır. Bu Quickstart'ta, şablon kullanarak basit bir Flask uygulaması oluşturursunuz. Ortaya çıkan proje Quickstart ile el ile oluşturduğunuz projeye benzer [- Flask ile bir web uygulaması oluşturun.](../ide/quickstart-python.md)

1. Visual Studio’yu çalıştırın.

1. Üst menü çubuğundan, "boş şişe" için **Yeni Proje** iletişim kutusunda **Yeni** > **New** > **Proje'yi**seçin, orta listedeki **Boş Flask Web Project** şablonunu seçin, projeye bir ad verin ve **Tamam'ı**seçin:

    ![Blank Flask Web Project şablonuyla yeni bir proje oluşturma](media/quickstart-python-06-blank-flask-template.png)

1. Visual Studio, bu projenin dış **paketler gerektirdiğini** belirten bir iletişim kutusu yla sizi ister. Şablon Flask'a bağımlılık belirten bir *requirements.txt* dosyası içerdiğinden bu iletişim kutusu görüntülenir. Visual Studio paketleri otomatik olarak yükleyebilir ve bunları sanal *bir ortama*yükleme seçeneği sunar. Genel bir ortama yükleme nin üzerinde sanal ortam kullanılması önerilir, bu nedenle devam etmek için **sanal ortama yükle'yi** seçin.

    ![Flask'ı sanal ortama yükleme](media/quickstart-python-07-install-into-virtual-environment.png)

1. Visual **Studio, Sanal Ortam Ekle** iletişim kutusunu görüntüler. Varsayılanı kabul edin ve **Oluştur'u**seçin, ardından yükseklik isteklerini onaylayın.

    > [!Tip]
    > Bir projeye başladığınızda, çoğu Visual Studio şablonunun sizi davet ettiğinden, hemen sanal bir ortam oluşturmanız önerilir. Sanal ortamlar, kitaplıkları ekler ken ve kaldırırken projenizin tam gereksinimlerini zaman içinde korur. Daha sonra, diğer geliştirme bilgisayarlarındaki (kaynak denetimi kullanırken olduğu gibi) ve projeyi bir üretim sunucusuna dağıtırken yeniden yüklemek için kullandığınız *bir requirements.txt* dosyasını kolayca oluşturabilirsiniz. Sanal ortamlar ve avantajları hakkında [Use virtual environments](../python/selecting-a-python-environment-for-a-project.md#use-virtual-environments) daha fazla bilgi için [bkz.](../python/managing-required-packages-with-requirements-txt.md)

1. Visual Studio bu ortamı oluşturduktan *sonra, requirements.txt*ile birlikte *app.py* bir dosyanız olduğunu görmek için **Solution Explorer'a** bakın. Şablonquickstart gibi kod sağladığını görmek için *app.py* açın [- Flask ile bir web uygulaması oluşturun](../ide/quickstart-python.md), birkaç eklenen bölümleri ile. Aşağıda gösterilen kodun tümü şablon tarafından oluşturulur, bu nedenle herhangi bir app.py *kendiniz* yapıştırmanız gerekmez.

    Kod gerekli içeri alma ile başlar:

    ```python
    from flask import Flask
    app = Flask(__name__)
    ```

    Sonraki bir web ana bilgisayara bir uygulama dağıtırken yararlı olabilir aşağıdaki satırdır:

    ```python
    wsgi_app = app.wsgi_app
    ```

    Sonra bir görünüm tanımlayan basit bir işlev üzerinde rota dekoratör geliyor:

    ```python
    @app.route('/')
    def hello():
        """Renders a sample page."""
        return "Hello World!"
    ```

    Son olarak, aşağıdaki başlangıç kodu, ana bilgisayar ve bağlantı noktasını zor kodlamak yerine ortam değişkenleri üzerinden ayarlamanızı sağlar. Bu kod, kodu değiştirmeden hem geliştirme hem de üretim makinelerinde yapılandırmayı kolayca kontrol etmenizi sağlar:

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

1. Uygulamayı çalıştırmak için **Hata** > **Ayıklama Başlatma'yı** seçin ve `localhost:5555`bir tarayıcıyı ' ya açın.

**Soru: Visual Studio başka ne gibi Python şablonları sunuyor?**

**Cevap**: Python iş yükü yüklüyken Visual Studio, [Flask, Bottle ve Django web çerçeveleri,](../python/python-web-application-project-templates.md)Azure bulut hizmetleri, farklı makine öğrenimi senaryoları ve hatta Python uygulaması içeren varolan bir klasör yapısından proje oluşturmak için bir şablon da dahil olmak üzere çeşitli proje şablonları sağlar. **Python** dil düğümünü ve alt düğümlerini seçerek**Dosya Yeni** > **Proje** iletişim **kutusundan** > bunlara erişebilirsiniz.

Visual Studio ayrıca python sınıfı, Python paketi, Python birim testi, *web.config* dosyaları ve daha fazlasını hızlı bir şekilde oluşturmak için çeşitli dosya veya *öğe şablonları* sağlar. Python projeniz açık olduğunda, **Project** > **Add New Item** menü komutu aracılığıyla öğe şablonlarına erişirsiniz. Madde [şablonları](python-item-templates.md) başvurusuna bakın.

Şablonları kullanmak, proje başlatırken veya dosya oluştururken size önemli bir zaman kazandırır ve farklı uygulama türleri ve kod yapıları hakkında bilgi edinmeniz için harika bir yoldur. Sunduklarına alışmak için çeşitli şablonlardan projeler ve öğeler oluşturmak birkaç dakikanızı alabilir.

**Soru: Cookiecutter şablonlarını da kullanabilir miyim?**

**Cevap**: Evet! Aslında Visual Studio, [Quickstart: Cookiecutter şablonundan bir proje oluşturma](../python/quickstart-04-python-in-visual-studio-project-from-cookiecutter.md)yoluyla öğrenebileceğiniz Cookiecutter ile doğrudan entegrasyon sağlar.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Öğretici: Visual Studio Python ile çalışma](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Varolan bir Python yorumlayıcıyı el ile tanımlama](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
- [Visual Studio 2015 ve önceki gün Python desteğini yükleyin](installing-python-support-in-visual-studio.md)
- [Konumları yükleme](installing-python-support-in-visual-studio.md#install-locations)
