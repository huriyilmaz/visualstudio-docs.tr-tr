---
title: Hızlı Başlangıç - Python kodu deposunu kopyalama
description: Bu hızlı başlangıçta, Visual Studio kullanarak Python koans deposunu kopyaarak bir Python projesi Visual Studio Takım Gezgini.
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
ms.openlocfilehash: 6ec913b78094ac9ad6649e019548e3785b939ba8
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726791"
---
# <a name="quickstart-clone-a-repository-of-python-code-in-visual-studio"></a>Hızlı Başlangıç: Visual Studio'da Python kodu Visual Studio

Visual Studio'da [Python desteğini yükledinizkten](installing-python-support-in-visual-studio.md)sonra, GitHub uzantısını Visual Studio. Uzantı, Python kodu deposunu kolayca kopyalamanızı ve IDE'nin içinde bu depodan bir proje oluşturmanıza olanak sağlar. Komut satırına depoları her zaman kopyalar ve daha sonra bu depolarla birlikte Visual Studio.

## <a name="install-the-github-extension-for-visual-studio"></a>Visual Studio için GitHub Uzantısını Visual Studio

[!INCLUDE[install-github-extension](includes/install-github-extension.md)]

## <a name="work-with-github-in-visual-studio"></a>Visual Studio'GitHub Visual Studio

1. Visual Studio.

1. Takım Gezgini'a bağlanarak Takım Gezgini veya depoyu kopyalayabilirsiniz GitHub Azure Repos'ı   >   seçin.  (Aşağıda gösterilen Bağlan **sayfasını** görmüyorsanız, üst araç çubuğunda sizi bu sayfaya kadar olan tak simgesini seçin.)

    ![Bir depoyu Azure Repos, GitHub ve kopyalamayı gösteren takım gezgini penceresi](media/team-explorer.png)

1. Yerel **Git Depoları** altında  Kopyala komutunu seçin, ardından URL alanına girin, kopyalanan dosyalar için bir klasör girin ve `https://github.com/gregmalcolm/python_koans` Kopyala **düğmesini** seçin.

    > [!Tip]
    > Dosyalarda belirttiğiniz **Takım Gezgini,** kopyalanan dosyaları almak için tam klasördür. Komutun aksine, Takım Gezgini otomatik olarak depo adıyla bir alt `git clone` klasör oluşturmaz. 

1. Kopyalama tamamlandığında, depo adı Yerel **Git Depoları listesinde** görünür. bu adla çift tıklar ve sonra da **Takım Gezgini.**

1. **Çözümler'in** altında Yeni'yi **seçin.**

    ![Takım gezgini penceresi, kopyadan yeni proje oluşturma](media/team-explorer-new-project.png)

1. Görüntülenen **Yeni Project** iletişim kutusunda **Python** diline gidin (veya "Python" araması yapmak), Mevcut **Python** Kodundan'ı  seçin, proje için bir ad belirtin, Konum'ı depoyla aynı klasöre ayarlayın ve Tamam'ı **seçin.** Görüntülenen sihirbazda Son'a **tıklayın.**

1. Menüden   >  **Çözüm Gezgini'yi** seçin.

1. Bu **Çözüm Gezgini** **python3** düğümünü genişletin, **contemplate_koans.py** dosyasına sağ tıklayın ve Başlangıç Dosyası Olarak **Ayarla'yı seçin.** Bu adım Visual Studio çalıştırması gereken dosyayı belirtir.

1. Menüden **Project** Koans Özellikleri'ne tıklayın, Genel sekmesini seçin ve  >   **Çalışma Dizini'yi** "python3" olarak ayarlayın.  Visual Studio çalışma dizini varsayılan olarak başlangıç dosyasının konumu yerine proje köküne (proje özelliklerinde de gördüğünüz *python3\contemplate_koans.py)* ayar olduğundan bu adım gereklidir. Program kodu, çalışma klasöründe *koans.txt* dosyasını aramasını sağlar, bu nedenle bu değeri değiştirmeden çalışma zamanı hatasıyla karşınız olur.

    ![Python projesi için çalışma dizinini ayarlama](media/projects-set-working-directory.png)

1. **Programı çalıştırmak için Ctrl** + **F5** **tuşlarına basın veya** Hata Ayıklama Olmadan  >  **Başlat'ı** seçin. koans.txtiçin **FileNotFoundError** *görüyorsanız,* önceki adımda açıklandığı gibi çalışma dizini ayarını kontrol edin.

1. Program başarıyla çalıştırıldı, *python3/koans/about_asserts.py'nin* 17. satırda onay hatası görüntüler. Bu kasıtlı bir durum: Program, tüm kasıtlı hataları düzeltmeniz için Python'a ders vermek üzere tasarlanmıştır. (Python Koans'a ilham [veren Ruby Koans](https://rubykoans.com/)hakkında daha fazla ayrıntı bulunabilir.)

    ![Python koans programından ilk çıkış](media/koans-output.png)

1. *Python3/koans/about_asserts.py* dosyasını açın, bu Çözüm Gezgini dosyaya  çift tıklayın. Satır numaralarının düzenleyicide varsayılan olarak görünmeyebilirsiniz. Bunu değiştirmek için Araçlar **Seçenekleri'ni** seçin, iletişim kutusunun alt kısmından Tüm ayarları göster'i seçin, ardından Metin Düzenleyici Python Genel'e gidin  >  ve Satır    >    >   **numaraları'na tıklayın:**

    ![Python dosyaları için satır numarasını açma](media/options-general-line-numbers.png)

1. 17. satırda bağımsız `False` değişken değerini olarak değiştirerek hatayı düzeltin. `True` Satırın aşağıdaki gibi okuması gerekir:

    ```python
    self.assertTrue(True) # This should be True
    ```

1. Programı yeniden çalıştırın. Hata Visual Studio sizi uyarıyorsa, kodu çalıştırmaya devam etmek **için Evet** ile yanıt verin. Ardından ilk denetimin başarılı olduğunu ve programın bir sonraki koan'da durduğuna bakabilirsiniz. Hataları ve programı istediğiniz gibi düzeltmeye devam edin.

> [!Important]
> Bu Hızlı Başlangıçta, python_koans deposundaki *GitHub.* Böyle bir depo yazarı tarafından doğrudan değişikliklerden korunur, bu nedenle değişiklikleri depoya işleme girişimi başarısız olur. Pratikte geliştiriciler, bu tür bir depoyu kendi GitHub hesaplarında yer alan bir deponun üzerine oluşturabilir, burada değişiklikler yapacak ve ardından bu değişiklikleri özgün depoya göndermek için çekme istekleri oluşturabilir. Kendi depo url'niz olduğunda, daha önce kullanılan özgün depo URL'si yerine URL'sini kullanın.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Öğretici: Python ile Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Mevcut Python yorumlayıcıyı el ile tanımlama](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
- [Visual Studio'da Python desteğini Windows](installing-python-support-in-visual-studio.md)
- [Yükleme konumları](installing-python-support-in-visual-studio.md#install-locations)
