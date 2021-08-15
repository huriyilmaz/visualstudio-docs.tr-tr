---
title: Hızlı Başlangıç - Python kod klasörü açma
description: Bu hızlı başlangıçta, bir Visual Studio projesi (yalnızca 2019'da) kullanmadan bir klasörden Python Visual Studio çalıştırabilirsiniz.
ms.date: 03/12/2019
ms.topic: quickstart
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.custom: seodec18
ms.workload:
- python
- data-science
monikerRange: '>= vs-2019'
ms.openlocfilehash: 2da3b76ee7a22e58431eafafa8600158a0ae9b18b12f3f4fc054f0aa0171ffea
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121245258"
---
# <a name="quickstart-open-and-run-python-code-in-a-folder"></a>Hızlı Başlangıç: Python kodunu bir klasörde açma ve çalıştırma

[Visual Studio 2019'da Python](installing-python-support-in-visual-studio.md)desteğini yüklediniz mi, mevcut Python kodunu Visual Studio 2019'da bir Visual Studio projesi oluşturmadan kolayca çalıştırabilirsiniz.

> [!Note]
> Visual Studio 2017 ve önceki sürümlerde, Python kodunu çalıştırmak için bir Visual Studio projesi oluşturmanız gerekir ve bunu yerleşik proje şablonunu kullanarak kolayca yapabilirsiniz. Bkz. [Hızlı Başlangıç: Mevcut koddan Python projesi oluşturma](quickstart-01-python-in-visual-studio-project-from-existing-code.md)

1. Bu kılavuzda, Python koduyla istediğiniz klasörü kullanabilirsiniz. Burada gösterilen örneği takip etmek için uygun bir klasördeki komutunu kullanarak gregmalcolm/python_koans GitHub deposunu `git clone https://github.com/gregmalcolm/python_koans` bilgisayarınıza kopyalayın.

1. 2019'Visual Studio'i açın ve başlangıç penceresinde, 2019'un **Kullanmaya başlayın** seçin.  Alternatif olarak, zaten Visual Studio Dosya Klasör **Aç**  >    >  **komutunu** seçin.

    ![Visual Studio başlangıç ekranı](media/quickstart-open-folder/01-open-local-folder.png)

1. Python kodunuzu içeren klasöre gidin ve Klasör **Seç'i seçin.** Uygulama kodunu kullanıyorsanız python_koans `python3` klasörünün içinde klasörü seçin.

    ![Klasör Aç komutundan Klasör Seç iletişim kutusu](media/quickstart-open-folder/02-select-folder.png)

1. Visual Studio Klasör Görünümü Çözüm Gezgini  içinde klasörü **görüntüler.** Klasör adlarının sol kenarlarında bulunan okları kullanarak klasörleri genişletebilirsiniz ve daraltabilirsiniz:

    ![Bir klasördeki klasörleri genişletme ve daraltma Çözüm Gezgini](media/quickstart-open-folder/03-expand-collapse-folders.png)

1. Bir Python klasörünü a Visual Studio, projeyle ilgili ayarları yönetmek için birkaç gizli klasör oluşturur. Bu klasörleri (ve *.git* klasörü gibi diğer gizli dosyaları ve klasörleri) görmek için Tüm Dosyaları **Göster araç çubuğu düğmesini** seçin:

    ![Çözüm Gezgini'de gizli klasörlerin görünümü](media/quickstart-open-folder/05-view-hidden-folders.png)

1. Kodu çalıştırmak için öncelikle başlangıç veya birincil program dosyasını tanımlamanız gerekir. Burada gösterilen örnekte başlangıç dosyası *contemplate-koans.py.* Bu dosyaya sağ tıklayın ve Başlangıç Öğesi Olarak **Ayarla'yı seçin.**

    ![Çözüm Gezgini'de bir başlangıç öğesi ayarlama](media/quickstart-open-folder/06-set-as-startup-item-command.png)

    > [!Important]
    > Başlangıç öğeniz açtığınız klasörün kökünde yer alıyorsa, Çalışma dizini ayarlama bölümünde açıklandığı gibi başlatma yapılandırması JSON dosyasına da bir satır [eklemeniz gerekir.](#set-a-working-directory)

1. **Ctrl** F5 tuşlarına basarak veya Hata Ayıklama Olmadan Başlat'ı +    >  **seçerek kodu çalıştırın.** Ayrıca, bir oynatma düğmesiyle başlangıç öğesini gösteren araç çubuğu düğmesini de seçerek hata ayıklayıcısında Visual Studio çalıştırabilirsiniz. Her durumda, Visual Studio öğenizin bir Python dosyası olduğunu algılar, bu nedenle varsayılan Python ortamında kodu otomatik olarak çalıştırır. (Bu ortam, araç çubuğunda başlangıç öğesinin sağ tarafından gösterilir.)

    ![Hata ayıklayıcısını başlat araç çubuğu düğmesi](media/quickstart-open-folder/07-start-debug-toolbar.png)

1. Programın çıkışı ayrı bir komut penceresinde görünür:

    ![Python kodunu çalıştırmaya ait çıkış penceresi](media/quickstart-open-folder/08-result-window.png)

1. Kodu farklı bir ortamda çalıştırmak için araç çubuğundaki açılan denetimden bu ortamı seçin ve ardından başlangıç öğesini yeniden çalıştırın.

1. Klasördeki klasörü kapatmak Visual Studio Dosya Klasörü **Kapat**  >  **menü** komutunu seçin.

## <a name="set-a-working-directory"></a>Çalışma dizini ayarlama

Varsayılan olarak Visual Studio, aynı klasörün kökünde klasör olarak açılan bir Python projesi çalıştırır. Ancak projenizin kodu, Python'ın bir alt klasör içinde çalıştırılı olduğunu varsayabilir. Örneğin, python_koans deposunun kök klasörünü açıp *python3/yer-koans.py* dosyasını başlangıç öğesi olarak ayarlayabilirsiniz. Ardından kodu çalıştırırsanız, dosyanın *bulunakoans.txt* bir hatayla karşılaştınız. Bu hatanın *nedeni contemplate-koans.py* Python'ın depo kökü yerine *python3* klasöründe çalıştırıldıklarını varsayıyor olmasıdır.

Böyle durumlarda, çalışma dizinini belirtmek için başlatma yapılandırması JSON dosyasına da bir satır eklemeniz gerekir:

1. içinde Python (*.py*) başlangıç dosyasına sağ **tıklayın ve Çözüm Gezgini Ayıkla ve** **Başlat'ı Ayarlar.**

    ![Contemplate-koans.py dosyasının seçili olduğu Çözüm Gezgini Klasör Görünümü'Ayarlar ve bağlam menüsünde Hata Ayıkla ve Başlat'ın seçili olduğu ekran görüntüsü.](media/quickstart-open-folder/09-debug-launch-settings-menu-command.png)

1. Görüntülenen Hata **ayıklayıcı seç** iletişim kutusunda Varsayılan'ı **ve ardından** Seç'i **seçin.**

    ![Varsayılan hata ayıklayıcının seçili olduğu ve Seç düğmesinin seçili olduğu Hata Ayıklayıcısı Seç iletişim kutusunun ekran görüntüsü.](media/quickstart-open-folder/10-select-debugger.png)

    > [!Note]
    > Varsayılan'ı seçenek olarak **görmüyorsanız** Hata Ayıkla ve Başlat komutlarını seçerek Python *.py* dosyasını **Ayarlar** olun. Visual Studio, hangi hata ayıklayıcısı seçeneklerinin görüntülen olduğunu belirlemek için dosya türünü kullanır.

1. Visual Studio, gizli *.vs* launch.vs.jsbulunan üzerindelaunch.vs.jsadlı bir dosya açar. Bu dosya, proje için hata ayıklama bağlamını açıklar. Çalışma dizini belirtmek için, `"workingDirectory"` python-koans örneğinde olduğu  `"workingDirectory": "python3"` gibi için bir değer ekleyin:

    ```json
    {
      "version": "0.2.1",
      "defaults": {},
      "configurations": [
        {
          "type": "python",
          "interpreter": "(default)",
          "interpreterArguments": "",
          "scriptArguments": "",
          "env": {},
          "nativeDebug": false,
          "webBrowserUrl": "",
          "project": "python3\\contemplate_koans.py",
          "name": "contemplate_koans.py",
          "workingDirectory": "python3"
        }
      ]
    }
    ```

1. Dosyayı kaydedin ve programı yeniden açın; bu program artık belirtilen klasörde çalışır.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Öğretici: Python ile Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Hızlı Başlangıç: Mevcut koddan Python projesi oluşturma](quickstart-01-python-in-visual-studio-project-from-existing-code.md)
- [Hızlı Başlangıç: Depodan Python projesi oluşturma](quickstart-03-python-in-visual-studio-project-from-repository.md)
- [Mevcut Python yorumlayıcıyı el ile tanımlama](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
