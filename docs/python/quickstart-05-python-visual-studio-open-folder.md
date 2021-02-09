---
title: Hızlı başlangıç-Python kod klasörünü açma
description: Bu hızlı başlangıçta, bir Visual Studio projesi kullanmadan bir klasörden Python kodu açar ve çalıştırırsınız (yalnızca Visual Studio 2019).
ms.date: 03/12/2019
ms.topic: quickstart
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
monikerRange: '>= vs-2019'
ms.openlocfilehash: bc47f2a91b0ce42c319651cad22dbe05fe32623f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99902411"
---
# <a name="quickstart-open-and-run-python-code-in-a-folder"></a>Hızlı başlangıç: bir klasörde Python kodunu açma ve çalıştırma

[Visual studio 2019 ' de Python desteğini](installing-python-support-in-visual-studio.md)yükledikten sonra visual Studio 2019 ' de var olan Python kodunu Visual Studio projesi oluşturmadan çalıştırmak kolaydır.

> [!Note]
> Visual Studio 2017 ve önceki sürümleri, Python kodunu çalıştırmak için bir Visual Studio projesi oluşturmanızı gerektirir, bu, kolayca yerleşik bir proje şablonu kullanarak yapabilirsiniz. Bkz [. hızlı başlangıç: mevcut koddan Python projesi oluşturma](quickstart-01-python-in-visual-studio-project-from-existing-code.md)

1. Bu izlenecek yol için, istediğiniz Python kodu ile herhangi bir klasörü kullanabilirsiniz. Burada gösterilen örnekle birlikte takip etmek için, uygun bir klasörde komutunu kullanarak gregmalcola/python_koans GitHub deposunu bilgisayarınıza kopyalayın `git clone https://github.com/gregmalcolm/python_koans` .

1. Visual Studio 2019 ' i başlatın ve başlangıç penceresinde, **Başlarken** sütununun en altında bulunan **Aç** ' ı seçin. Alternatif olarak, zaten Visual Studio çalıştırıyorsanız, bunun yerine **Dosya**  >  **Aç**  >  **klasörünü** seçin.

    ![Visual Studio başlangıç ekranı](media/quickstart-open-folder/01-open-local-folder.png)

1. Python kodunuzu içeren klasöre gidin ve ardından **Klasör Seç**' i seçin. Python_koans kodu kullanıyorsanız, `python3` kopya klasörü içindeki klasörü seçtiğinizden emin olun.

    ![Klasörü aç komutundan Klasör Seç iletişim kutusu](media/quickstart-open-folder/02-select-folder.png)

1. Visual Studio, klasör **görünümü** olarak adlandırılan **Çözüm Gezgini** klasörü görüntüler. Klasör adlarının sol kenarlarındaki okları kullanarak klasörleri genişletebilir ve daraltabilirsiniz:

    ![Çözüm Gezgini klasörleri genişletme ve daraltma denetimleri](media/quickstart-open-folder/03-expand-collapse-folders.png)

1. Python klasörünü açarken, Visual Studio projeyle ilgili ayarları yönetmek için birkaç gizli klasör oluşturur. Bu klasörleri (ve *. git* klasörü gibi diğer gizli dosya ve klasörleri) görmek Için **tüm dosyaları göster** araç çubuğu düğmesini seçin:

    ![Çözüm Gezgini içindeki gizli klasörlerin görünümü](media/quickstart-open-folder/05-view-hidden-folders.png)

1. Kodu çalıştırmak için öncelikle başlangıç veya birincil program dosyasını belirlemeniz gerekir. Burada gösterilen örnekte, *Contemplate-koans.py* başlangıç dosyası. Bu dosyaya sağ tıklayın ve **Başlangıç öğesi olarak ayarla**' yı seçin.

    ![Çözüm Gezgini bir başlangıç öğesi ayarlama](media/quickstart-open-folder/06-set-as-startup-item-command.png)

    > [!Important]
    > Başlangıç öğesi açtığınız klasörün kökünde bulunmuyorsa, [çalışma dizini ayarlama](#set-a-working-directory)bölümünde açıklandığı gibi başlatma yapılandırma JSON dosyasına bir satır da eklemeniz gerekir.

1. Kodu **CTRL** + **F5** tuşuna basarak veya **hata ayıklama**  >  **başlatma hatası olmadan Başlat**' a seçerek çalıştırın. Ayrıca, Visual Studio hata ayıklayıcısında kod çalıştıran bir Play düğmesine sahip başlangıç öğesini gösteren araç çubuğu düğmesini seçebilirsiniz. Her durumda, Visual Studio başlangıç öğesinin bir Python dosyası olduğunu algılar, bu yüzden kodu varsayılan Python ortamında otomatik olarak çalıştırır. (Bu ortam, araç çubuğundaki başlangıç öğesinin sağında gösterilir.)

    ![Hata ayıklayıcı araç çubuğu düğmesi Başlat](media/quickstart-open-folder/07-start-debug-toolbar.png)

1. Programın çıktısı ayrı bir komut penceresinde görünür:

    ![Python kodu çalıştırmak için çıkış penceresi](media/quickstart-open-folder/08-result-window.png)

1. Kodu farklı bir ortamda çalıştırmak için, araç çubuğundaki açılan denetimden bu ortamı seçin, sonra başlangıç öğesini yeniden başlatın.

1. Visual Studio 'da klasörü kapatmak için **Dosya**  >  **klasörü kapat** menü komutunu seçin.

## <a name="set-a-working-directory"></a>Çalışma dizini ayarlama

Varsayılan olarak, Visual Studio aynı klasörün kökünde bir klasör olarak açılan bir Python projesi çalıştırır. Ancak projenizdeki kod, Python 'un bir alt klasörde çalıştırıldığını varsayabilir. Örneğin, python_koans deposunun kök klasörünü açıp *python3/Contemplate-koans. Kopyala* dosyasını başlangıç öğesi olarak ayarladığınızı varsayalım. Daha sonra kodu çalıştırırsanız *koans.txt* dosyanın bulunamadığını belirten bir hata görürsünüz. Bu hata, *Contemplate-koans.py* Python 'un depo kökü yerine *python3* klasöründe çalıştırıldığını varsaydığı için oluşur.

Bu gibi durumlarda, çalışma dizinini belirtmek için başlatma yapılandırma JSON dosyasına bir satır da eklemeniz gerekir:

1. **Çözüm Gezgini** ' de Python (*. Kopyala*) başlangıç dosyasına sağ tıklayın ve **Hata Ayıkla ve başlatma ayarları**' nı seçin.

    ![Contemplate-koans.py dosyası seçili olan Çözüm Gezgini klasör görünümünün ekran görüntüsü ve bağlam menüsünde hata ayıklama ve başlatma ayarları seçili.](media/quickstart-open-folder/09-debug-launch-settings-menu-command.png)

1. Görüntülenen **hata ayıklayıcı Seç** iletişim kutusunda, **varsayılan** ' ı seçin ve ardından **Seç**' i seçin.

    ![Varsayılan hata ayıklayıcı seçiliyken hata ayıklayıcı Seç iletişim kutusunun ekran görüntüsü ve Seç düğmesi seçili.](media/quickstart-open-folder/10-select-debugger.png)

    > [!Note]
    > **Varsayılan** olarak bir seçenek olarak görmüyorsanız, **hata ayıklama ve başlatma ayarları** komutunu seçerken bir Python *. Kopyala* dosyası seçtiğinizden emin olun. Visual Studio, görüntülenecek hata ayıklayıcı seçeneklerini belirleyen dosya türünü kullanır.

1. Visual Studio, Hidden *. vs* klasöründe bulunan *launch.vs.jsüzerinde* adlı bir dosya açar. Bu dosya, projenin hata ayıklama bağlamını açıklar. Çalışma dizini belirtmek için, `"workingDirectory"`  `"workingDirectory": "python3"` Python-koans örneğinde olduğu gibi için bir değer ekleyin:

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
> [Öğretici: Visual Studio 'da Python ile çalışma](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Hızlı başlangıç: mevcut koddan bir Python projesi oluşturma](quickstart-01-python-in-visual-studio-project-from-existing-code.md)
- [Hızlı başlangıç: bir depodan Python projesi oluşturma](quickstart-03-python-in-visual-studio-project-from-repository.md)
- [Mevcut bir Python yorumlayıcısını el ile tanımla](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
