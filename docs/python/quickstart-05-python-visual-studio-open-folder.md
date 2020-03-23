---
title: Quickstart - Python kod klasörü açma
description: Bu hızlı başlangıçta, Visual Studio projesini (yalnızca Visual Studio 2019) kullanmadan Python kodunu bir klasörden açıp çalıştırabilirsiniz.
ms.date: 03/12/2019
ms.topic: quickstart
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
monikerRange: '>= vs-2019'
ms.openlocfilehash: ab234d9482cf9cbab49c15167ea45aff9ac2c7e6
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "62431166"
---
# <a name="quickstart-open-and-run-python-code-in-a-folder"></a>Quickstart: Python kodunu bir klasörde açın ve çalıştırın

Visual Studio [2019'a Python desteğini yükledikten](installing-python-support-in-visual-studio.md)sonra Visual Studio 2019'da visual studio 2019'da visual studio projesi oluşturmadan mevcut Python kodunu çalıştırmak kolaydır.

> [!Note]
> Visual Studio 2017 ve daha önce, yerleşik proje şablonunu kullanarak kolayca yapabileceğiniz Python kodunu çalıştırmak için bir Visual Studio projesi oluşturmanız gerekir. Bkz. [Hızlı Başlangıç: Varolan koddan bir Python projesi oluşturma](quickstart-01-python-in-visual-studio-project-from-existing-code.md)

1. Bu izbin için, istediğiniz Python koduna sahip herhangi bir klasörü kullanabilirsiniz. Burada gösterilen örnekle birlikte takip etmek için, uygun bir klasördeki komutu `git clone https://github.com/gregmalcolm/python_koans` kullanarak gregmalcolm/python_koans GitHub deposunu bilgisayarınıza kopyalayınız.

1. Visual Studio 2019'u başlatın ve başlangıç penceresinde **Başlat** sütununun altındaki **Aç'ı** seçin. Alternatif olarak, Visual Studio zaten çalışıyorsa, bunun yerine **Dosya** > **Aç** > **Klasörkomutunu** seçin.

    ![Visual Studio başlangıç ekranı](media/quickstart-open-folder/01-open-local-folder.png)

1. Python kodunuzu içeren klasöre gidin ve ardından **Klasörü Seç'i**seçin. python_koans kodunu kullanıyorsanız, klon klasöründeki `python3` klasörü seçtiğinizden emin olun.

    ![Klasörü Aç komutundan Klasör seç iletişim kutusu](media/quickstart-open-folder/02-select-folder.png)

1. Visual Studio klasörü **Solution Explorer'da** **Klasör Görünümü**olarak adlandırılan yerde görüntüler. Klasör adlarının sol kenarlarındaki okları kullanarak klasörleri genişletebilir ve daraltabilirsiniz:

    ![Solution Explorer'da klasörleri genişletmek ve daraltmak için denetimler](media/quickstart-open-folder/03-expand-collapse-folders.png)

1. Bir Python klasörünü açarken Visual Studio, projeyle ilgili ayarları yönetmek için birkaç gizli klasör oluşturur. Bu klasörleri (ve *.git* klasörü gibi diğer gizli dosya ve klasörleri) görmek için **Tüm Dosyaları Göster** araç çubuğunu seçin:

    ![Çözüm Gezgini'ndeki gizli klasörlerin görünümü](media/quickstart-open-folder/05-view-hidden-folders.png)

1. Kodu çalıştırmak için öncelikle başlangıç veya birincil program dosyasını tanımlamanız gerekir. Burada gösterilen örnekte, başlangıç dosyası *contemplate-koans.py.* Bu dosyaya sağ tıklayın ve **Başlangıç Öğesi olarak Ayarla'yı**seçin.

    ![Solution Explorer'da başlangıç öğesi ayarlama](media/quickstart-open-folder/06-set-as-startup-item-command.png)

    > [!Important]
    > Başlangıç öğeniz açtığınız klasörün kökünde bulunmuyorsa, bölümdeki açıklandığı gibi başlatma yapılandırması JSON dosyasına da bir satır eklemeniz gerekir, [Çalışma dizini ayarlayın.](#set-a-working-directory)

1. **Ctrl**+**F5** tuşuna basarak veya Hata **Ayıklama** > Başlatma'yı hata ayıklama olmadan seçerek kodu**çalıştırın.** Ayrıca, Visual Studio hata ayıklayıcıda kod çalıştıran bir oynatma düğmesiyle başlangıç öğesini gösteren araç çubuğu düğmesini de seçebilirsiniz. Her durumda Visual Studio başlangıç öğenizin bir Python dosyası olduğunu algılar, böylece kodu varsayılan Python ortamında otomatik olarak çalıştırZ. (Bu ortam, araç çubuğundaki başlangıç öğesinin sağında gösterilir.)

    ![Hata ayıklama araç çubuğu düğmesini başlat](media/quickstart-open-folder/07-start-debug-toolbar.png)

1. Programın çıktısı ayrı bir komut penceresinde görünür:

    ![Python kodunu çalıştırmak için çıkış penceresi](media/quickstart-open-folder/08-result-window.png)

1. Kodu farklı bir ortamda çalıştırmak için, araç çubuğundaki açılır denetimden bu ortamı seçin ve ardından başlangıç öğesini yeniden başlatın.

1. Visual Studio'daki klasörü kapatmak için **Dosya** > **Kapat klasörü** menüsü komutunu seçin.

## <a name="set-a-working-directory"></a>Çalışma dizini ayarlama

Varsayılan olarak, Visual Studio aynı klasörün kökünde klasör olarak açılmış bir Python projesini çalıştırın. Ancak projenizdeki kod, Python'un bir alt klasörde çalıştırıldığını varsayabilir. Örneğin, python_koans deposunun kök klasörünü açtığınızı ve *python3/contemplate-koans.py* dosyasını başlangıç öğesi olarak ayarladığınızı varsayalım. Daha sonra kodu çalıştırırsanız, *koans.txt* dosyasının bulunamadığı bir hata görürsünüz. Bu hata, *contemplate-koans.py* Python'un depo kökü yerine *python3* klasöründe çalıştırıldığını varsaydığından kaynaklanır.

Bu gibi durumlarda, çalışma dizinini belirtmek için başlatma yapılandırması JSON dosyasına bir satır eklemeniz gerekir:

1. **Solution Explorer'daki** Python (*.py*) başlangıç dosyasına sağ tıklayın ve **Hata Ayıklama ve Başlatma Ayarları'nı**seçin.

    ![Python dosyası için Hata Ayıklama ve Başlatma Ayarları komutu](media/quickstart-open-folder/09-debug-launch-settings-menu-command.png)

1. Görünen **hata ayıklama** kutusunu seç, **Varsayılan'ı** seçin ve sonra **Seç'i**seçin.

    ![Python dosyası için Hata Ayıklama ve Başlatma Ayarları komutu](media/quickstart-open-folder/10-select-debugger.png)

    > [!Note]
    > **Varsayılan'ı** bir seçenek olarak görmüyorsanız, **Hata Ayıklama ve Başlatma Ayarları** komutunu seçerken Python *.py* dosyasını sağ tıklattığınızdan emin olun. Visual Studio, görüntülenecek hata ayıklama seçeneklerini belirlerken dosya türünü kullanır.

1. Visual Studio, gizli *.vs* klasöründe bulunan *launch.vs.json*adlı bir dosyayı açar. Bu dosya, projenin hata ayıklama bağlamını açıklar. Çalışma dizini belirtmek için, `"workingDirectory"`python-koans örneğinde olduğu `"workingDirectory": "python3"` gibi bir değer ekleyin:

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

1. Dosyayı kaydedin ve şimdi belirtilen klasörde çalışan programı yeniden başlatın.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Öğretici: Visual Studio Python ile çalışma](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Hızlı başlatma: Varolan koddan bir Python projesi oluşturma](quickstart-01-python-in-visual-studio-project-from-existing-code.md)
- [Hızlı başlangıç: Bir depodan Python projesi oluşturma](quickstart-03-python-in-visual-studio-project-from-repository.md)
- [Varolan bir Python yorumlayıcıyı el ile tanımlama](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
