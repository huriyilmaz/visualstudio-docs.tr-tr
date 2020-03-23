---
title: Quickstart - Python kodunun deposunu klonlama
description: Bu hızlı başlangıçta, Visual Studio Team Explorer'ı kullanarak Python koans deposunu klonlayarak Visual Studio'da bir Python projesi oluşturursunuz.
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
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "64543147"
---
# <a name="quickstart-clone-a-repository-of-python-code-in-visual-studio"></a>Quickstart: Visual Studio'da Python kodunun deposunu klonlayın

[Visual Studio'ya Python desteğini yükledikten](installing-python-support-in-visual-studio.md)sonra Visual Studio için GitHub Uzantısı'nı ekleyebilirsiniz. Uzantı, Python kodunun deposunu kolayca klonlamanızı ve IDE içinden bir proje oluşturmanızı sağlar. Her zaman komut satırında da depoları klonlayabilir ve daha sonra Visual Studio'da onlarla çalışabilirsiniz.

## <a name="install-the-github-extension-for-visual-studio"></a>Visual Studio için GitHub Uzantısını yükleyin

[!INCLUDE[install-github-extension](includes/install-github-extension.md)]

## <a name="work-with-github-in-visual-studio"></a>Visual Studio'da GitHub ile çalışın

1. Visual Studio’yu başlatın.

1. GitHub veya Azure Repos'a bağlanabileceğiniz veya bir depoyu klonlayabildiğiniz **Takım Gezgini** penceresini açmak için Takım Gezgini'ni **Görüntüle'yi** > **Team Explorer** seçin. (Aşağıda gösterilen **Bağlan** sayfasını görmüyorsanız, sizi o sayfaya götüren üst araç çubuğundaki fiş simgesini seçin.)

    ![Azure Repos, GitHub ve bir depoyu klonlama gösteren takım gezgini penceresi](media/team-explorer.png)

1. **Yerel Git Depoları** **altında, Klon** komutunu seçin, ardından URL alanına girin, `https://github.com/gregmalcolm/python_koans` klonlanan dosyalar için bir klasör girin ve **Klon** düğmesini seçin.

    > [!Tip]
    > **Takım Gezgini'nde** belirttiğiniz klasör, klonlanan dosyaları almak için tam klasördür. Komutun `git clone` aksine, **Team Explorer'da** bir klon oluşturmak otomatik olarak deponun adını içeren bir alt klasör oluşturmaz.

1. Klonlama tamamlandığında, depo adı **Yerel Git Depoları** listesinde görünür. **Takım**Gezgini'ndeki depo panosuna gitmek için bu adı çift tıklatın.

1. **Çözümler**altında, **Yeni'yi**seçin.

    ![Takım gezgini penceresi, klondan yeni bir proje oluşturma](media/team-explorer-new-project.png)

1. Görünen **Yeni Proje** iletişim kutusunda, **Python** diline gidin (veya "Python"da arama yapın), **Varolan Python Kodundan**seçin, proje için bir ad belirtin, **Konum'u** depoyla aynı klasöre ayarlayın ve **Tamam'ı**seçin. Görünen sihirbazda **Finish'i**seçin.

1. Menüden**Çözüm Gezgini'ni** **Görüntüle'yi** > seçin.

1. **Çözüm Gezgini'nde** **python3** düğümünü genişletin, **contemplate_koans.py'ye**sağ tıklayın ve **Başlangıç Dosyası olarak Ayarla'yı**seçin. Bu adım Visual Studio'ya projeyi çalıştırırken hangi dosyayı kullanması gerektiğini söyler.

1. Menüden **Project** > **Koans Properties'i** seçin, **Genel** sekmesini seçin ve **Çalışma Dizini'ni** "python3" olarak ayarlayın. Bu adım, varsayılan olarak Visual Studio başlangıç dosyasının konumu yerine proje köküne çalışma dizini ayarlar çünkü *(python3\contemplate_koans.py*, proje özellikleri de görebilirsiniz). Program kodu çalışma klasöründe bir dosya *koans.txt* arar, bu nedenle bu değeri değiştirmeden bir çalışma zamanı hatası bakın.

    ![Python projesi için çalışma dizinini ayarlama](media/projects-set-working-directory.png)

1. **Ctrl**+**F5** tuşuna basın veya programı çalıştırmak için Hata Ayıklama olmadan **Hata Ayıklama** > **Başlat'ı** seçin. *Koans.txt*için bir **FileNotFoundError** görürseniz, önceki adımda açıklandığı gibi çalışma dizini ayarını denetleyin.

1. Program başarılı bir şekilde çalıştığında, *python3/koans/about_asserts.py*satırında bir iddia hatası görüntüler. Bu kasıtlı: program tüm kasıtlı hataları düzeltmek zorunda Python öğretmek için tasarlanmıştır. (Daha fazla bilgi [Ruby Koans](https://rubykoans.com/)bulunur , Hangi Python Koans ilham.)

    ![Python koans programından ilk çıktı](media/koans-output.png)

1. **Solution Explorer'da** gezinmeve dosyayı çift tıklatarak *python3/koans/about_asserts.py'yi* açın. Satır numaralarının varsayılan olarak düzenleyicide görünmediğini unutmayın. Bunu değiştirmek için **Araçlar** > **Seçenekleri'ni**seçin, iletişim kutusunun altındaki tüm **ayarları göster'i** seçin, ardından Text **Editor** > **Python** > **General'a** gidin ve **Satır numaralarını**seçin:

    ![Python dosyaları için satır numarasını açma](media/options-general-line-numbers.png)

1. Satır 17'deki `False` bağımsız değişkeni `True`'' ye değiştirerek hatayı düzeltin Satır aşağıdaki gibi okunmalıdır:

    ```python
    self.assertTrue(True) # This should be True
    ```

1. Programı yeniden çalıştırın. Visual Studio sizi hatalar konusunda uyarırsa, kodu çalıştırmaya devam etmek için **Evet** ile yanıt verin. Daha sonra ilk çek geçer ve program sonraki koan üzerinde durur bakın. Hataları ve programı istediğiniz gibi düzeltmeye devam edin.

> [!Important]
> Bu Quickstart'ta, GitHub'daki *python_koans* deposunun doğrudan bir klonunu oluşturdunuz. Böyle bir depo, yazarı tarafından doğrudan değişikliklere karşı korunur, bu nedenle depoda değişiklik yapmaya çalışmak başarısız olur. Uygulamada, geliştiriciler bunun yerine kendi GitHub hesabına böyle bir depo çatal, orada değişiklik yapmak ve daha sonra özgün deposuna bu değişiklikleri göndermek için çekme istekleri oluşturmak. Kendi çatalınız olduğunda, daha önce kullanılan orijinal depo URL'si yerine URL'sini kullanın.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Öğretici: Visual Studio Python ile çalışma](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Varolan bir Python yorumlayıcıyı el ile tanımlama](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
- [Windows'da Visual Studio'da Python desteği nasıl yüklenir?](installing-python-support-in-visual-studio.md)
- [Konumları yükleme](installing-python-support-in-visual-studio.md#install-locations)
