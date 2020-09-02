---
title: Hızlı başlangıç-Python kodu deposunu kopyalama
description: Bu hızlı başlangıçta, Visual Studio Takım Gezgini kullanarak Python koans deposunu kopyalayarak Visual Studio 'da bir Python projesi oluşturacaksınız.
ms.date: 12/06/2018
ms.topic: quickstart
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 5d0363626748588b6f4058e197f0d6796ece51ee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64543147"
---
# <a name="quickstart-clone-a-repository-of-python-code-in-visual-studio"></a>Hızlı başlangıç: Visual Studio 'da Python kodu deposunu kopyalama

[Visual Studio 'Da Python desteğini](installing-python-support-in-visual-studio.md)yükledikten sonra Visual Studio Için GitHub uzantısını ekleyebilirsiniz. Uzantı, Python kodu deposunu kolayca kopyalayıp IDE içinden bir proje oluşturmanıza olanak sağlar. Her zaman komut satırındaki depoları kopyalayabilir ve ardından Visual Studio 'da bunlarla çalışabilirsiniz.

## <a name="install-the-github-extension-for-visual-studio"></a>Visual Studio için GitHub uzantısını yükler

[!INCLUDE[install-github-extension](includes/install-github-extension.md)]

## <a name="work-with-github-in-visual-studio"></a>Visual Studio 'da GitHub ile çalışma

1. Visual Studio 'Yu başlatın.

1. **View**  >  GitHub veya Azure Repos 'e bağlanabildiğinizi veya bir depoyu klonlayabileceğiniz **Takım Gezgini** penceresini açmak için**Takım Gezgini** görüntüle ' yi seçin. (Aşağıda gösterilen **Bağlan** sayfasını görmüyorsanız, en üstteki araç çubuğunda yer alan tak simgesini seçin ve bu sayfaya gidersiniz.)

    ![Bir depoyu Azure Repos, GitHub ve kopyalamayı gösteren Takım Gezgini penceresi](media/team-explorer.png)

1. **Yerel Git depoları**altında, **Kopyala** komutunu seçin, sonra `https://github.com/gregmalcolm/python_koans` URL alanına girin, kopyalanmış dosyalar Için bir klasör girin ve **Kopyala** düğmesini seçin.

    > [!Tip]
    > **Takım Gezgini** içinde belirttiğiniz klasör klonlanan dosyaları almak için tam klasördür. Komutun aksine `git clone` , **Takım Gezgini** bir kopyanın oluşturulması, otomatik olarak deponun adı ile bir alt klasör oluşturmaz.

1. Kopyalama tamamlandığında, Depo adı **yerel Git depoları** listesinde görünür. **Takım Gezgini**içindeki depo panosuna gitmek için bu ada çift tıklayın.

1. **Çözümler**altında **Yeni**' yi seçin.

    ![Takım Gezgini penceresi, bir kopyadan yeni bir proje oluşturma](media/team-explorer-new-project.png)

1. Görüntülenen **Yeni proje** iletişim kutusunda, **Python** diline gidin (veya "Python" üzerinde arama yapın), **varolan Python kodundan**seçim yapın, proje için bir ad belirleyin, **konumu** depoyla aynı klasöre ayarlayın ve **Tamam**' ı seçin. Görüntülenen sihirbazda **son**' u seçin.

1. Menüden **Görünüm**  >  **Çözüm Gezgini** seçin.

1. **Çözüm Gezgini**' de, **python3** düğümünü genişletin, **contemplate_koans. Kopyala**' ya sağ tıklayın ve **başlangıç dosyası olarak ayarla**' yı seçin. Bu adım, Visual Studio 'Nun projeyi çalıştırırken hangi dosyayı kullanması gerektiğini söyler.

1. Menüden **Proje**  >  **koans özelliklerini** seçin, **genel** sekmesini seçin ve **çalışma dizinini** "python3" olarak ayarlayın. Bu adım gereklidir çünkü varsayılan olarak Visual Studio, çalışma dizinini başlangıç dosyasının konumu yerine proje köküne ayarlar (*python3 \ contemplate_koans. Kopyala*) ve bu, proje özelliklerinde de görebilirsiniz). Program kodu çalışma klasöründeki bir dosya *koans.txt* arar, bu nedenle bu değeri değiştirmeden bir çalışma zamanı hatası görürsünüz.

    ![Python projesi için çalışma dizinini ayarlama](media/projects-set-working-directory.png)

1. **Ctrl** + Programı çalıştırmak için CTRL**F5** tuşuna basın veya **hata ayıklama**  >  **olmadan Başlat** ' ı seçin. *koans.txt*Için bir **filenotfounbir** görürseniz, önceki adımda açıklandığı gibi çalışma dizini ayarını kontrol edin.

1. Program başarıyla çalıştırıldığında, 17. satırdaki *python3/koans/about_asserts. Kopyala*üzerinde bir onaylama hatası görüntüler. Bu bilerek yapılır: program, kasıtlı olarak tüm hataları düzelterek Python 'a öğretmek için tasarlanmıştır. (Python koans 'da daha fazla ayrıntı için bkz. [Ruby](https://rubykoans.com/)'ler.)

    ![Python koans programından ilk çıkış](media/koans-output.png)

1. *Python3/koans/about_asserts. kopyala* **Çözüm Gezgini** ' yı açın ve dosyaya çift tıklayın. Satır numaralarının düzenleyicide varsayılan olarak görünmediğine dikkat edin. Bunu değiştirmek için **Araçlar**  >  **Seçenekler**' i seçin, iletişim kutusunun alt kısmındaki **tüm ayarları göster** ' i seçin, sonra **metin Düzenleyicisi**  >  **Python**  >  **genel** ' e gidin ve **satır numaraları**' nı seçin:

    ![Python dosyaları için satır numarası açılıyor](media/options-general-line-numbers.png)

1. `False`17. satırdaki bağımsız değişkeni değiştirerek hatayı düzeltin `True` . Satır aşağıdaki gibi okunmalıdır:

    ```python
    self.assertTrue(True) # This should be True
    ```

1. Programı yeniden çalıştırın. Visual Studio hatalar hakkında sizi uyaralıyorsa, kodu çalıştırmaya devam etmek için **Evet** ile yanıtlayın. Ardından ilk çekin başarılı olduğunu ve programın bir sonraki Koa 'da durmasını görürsünüz. Hataları ve programı dilediğiniz gibi düzeltmeye devam edin.

> [!Important]
> Bu hızlı başlangıçta, GitHub 'da *python_koans* deposunun doğrudan bir kopyasını oluşturdunuz. Böyle bir depo, yazar tarafından doğrudan değişikliklerden korunur, bu nedenle değişiklikleri depoya kaydetmeye çalışmak başarısız olur. Pratikte, geliştiriciler bu tür bir depoyu kendi GitHub hesaplarına çatalla, orada değişiklik yapıp, ardından bu değişiklikleri orijinal depoya göndermek için çekme istekleri oluşturacak. Kendi çatalınız olduğunda, daha önce kullanılan özgün depo URL 'si yerine URL 'sini kullanın.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Öğretici: Visual Studio 'da Python ile çalışma](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Mevcut bir Python yorumlayıcısını el ile tanımla](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
- [Windows üzerinde Visual Studio 'da Python desteği nasıl yüklenir](installing-python-support-in-visual-studio.md)
- [Konum yüklemeleri](installing-python-support-in-visual-studio.md#install-locations)
