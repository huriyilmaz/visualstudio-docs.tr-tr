---
title: Karışık mod Python/C++ hata ayıklaması için semboller
description: Nasıl Visual Studio, tam karma mod C++ ve Python hata ayıklaması için sembolleri yükleme olanağı sağlar.
ms.date: 11/12/2018
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.workload:
- python
- data-science
ms.openlocfilehash: aaf6fd34544714444afef5d4a9bea8d4aa827afd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122038571"
---
# <a name="install-debugging-symbols-for-python-interpreters"></a>Python yorumlayıcıları için hata ayıklama sembollerini yükleme

Tam hata ayıklama deneyimi sağlamak için, Visual Studio [modundaki Python](debugging-mixed-mode-c-cpp-python-in-visual-studio.md) hata ayıklayıcısının çok sayıda iç veri yapısını ayrıştırmak için kullanılan Python yorumlayıcısı için hata ayıklama sembollerine ihtiyacı vardır. Örneğin *python27.dll,* karşılık gelen sembol dosyası *python27.pdb'dir;* için *python36.dll,* sembol dosyası *python36.pdb'dir.* Yorumlayıcının her sürümü, çeşitli modüller için sembol dosyaları da sağlar.

Visual Studio 2017 ve sonraki bir sürümü ile Python 3 ve Anaconda 3 yorumlayıcıları ilgili sembolleri otomatik olarak yük Visual Studio bu sembolleri otomatik olarak bulur. 2015 Visual Studio önceki sürümler için veya diğer yorumlayıcıları kullanırken, simgeleri ayrı ayrı indirmeniz ve ardından Visual Studio Hata Ayıklama Sembolleri sekmesindeki Araçlar Seçenekleri iletişim kutusu aracılığıyla bunları işaret  >     >   edin. Bu adımlar aşağıdaki bölümlerde ayrıntılı olarak açıklanmıştır.

Visual Studio, genellikle karma mod hata ayıklama oturumu başlatma sırasında sembollere ihtiyaç olduğunda size sorabilirsiniz. Bu durumda, iki seçeneği olan bir iletişim kutusu görüntüler:

- **Sembol ayarlarını aç iletişim kutusu,** **Hata Ayıklama** Sembolleri **sekmesinin Seçenekler** iletişim  >  **kutusunu** açar.
- **Yorumlayıcım için sembolleri** indir bu mevcut belge sayfasını açar; bu durumda Araçlar Seçenekleri'ne tıklayın ve devam etmek için  >   **Hata Ayıklama**  >  **Sembolleri sekmesine** gidin.

    ![Karma mod hata ayıklayıcısı sembolleri istemi](media/mixed-mode-debugging-symbols-required.png)

## <a name="download-symbols"></a>Sembolleri indirme

- Python 3.5 ve sonraki sürümler: Python yükleyicisi aracılığıyla hata ayıklama sembolleri alın. Özel **yükleme'yi** seçin, **İleri'yi** seçerek Gelişmiş  Seçenekler'e **bakın,** ardından Hata ayıklama sembollerini indir ve Hata ayıklama ikililerini indir **kutularını seçin:**

    ![Hata ayıklama sembolleri içeren Python 3.x yükleyicisi](media/mixed-mode-debugging-symbols-installer35.png)

    Sembol dosyaları (*.pdb*) daha sonra kök yükleme klasöründe bulunur (tek tek modüllerin sembol dosyaları *DALL'ler* klasöründe bulunur). Bu nedenle, Visual Studio otomatik olarak bulur ve başka bir adım gerekmez.

- Python 3.4.x ve önceki sürümler: Semboller, resmi *dağıtımlardan veya* [Enthought Canopy'den](#enthought-canopy).zipindirilebilir dosyalar olarak kullanılabilir. [](#official-distributions) İndirdikten sonra, python klasörünün içindeki Semboller klasörü gibi devam etmek *için* dosyaları yerel bir klasöre ayıklayın.

    > [!Important]
    > Simgeler, Python'ın küçük derlemeleri ile 32 bit ile 64 bit derlemeler arasında farklılık gösterir, bu nedenle sürümleri tam olarak eşleşmesi gerekir. Kullanılan yorumlayıcıyı kontrol etmek için projenizin altındaki **Python Ortamları**  düğümünü genişletin **Çözüm Gezgini** adını not edin. Ardından Python Ortamları **penceresine geçebilirsiniz**  ve yükleme konumunu not edersiniz. Ardından bu konumda bir komut penceresi açın *vepython.exe* sürümünü ve 32 bit mi yoksa 64 bit mi olduğunu gösteren komutunu açın.

- ActiveState Python gibi diğer tüm üçüncü taraf Python dağıtımları için: bu dağıtımın yazarlarına ulaşın ve size semboller sağlamalarını talepte bulunanlar. WinPython, standart Python yorumlayıcısını değişiklik yapmadan içerir, bu nedenle ilgili sürüm numarası için resmi dağıtımdan sembolleri kullanın.

## <a name="point-visual-studio-to-the-symbols"></a>Simgeleri Visual Studio işaret etmek

Sembolleri ayrı olarak indirdiysanız, bunları daha iyi Visual Studio aşağıdaki adımları izleyin. Python 3.5 veya sonraki bir sürümü yükleyicisi aracılığıyla semboller yüklemiş Visual Studio otomatik olarak bulur.

1. Araçlar Seçenekler **menüsünü**  >  **seçin** ve Hata Ayıklama **Sembolleri'ne**  >  **gidin.**

1. Araç **çubuğunda** Ekle düğmesini seçin (aşağıda özetlenmiştir), indirilen sembolleri genişletdiğiniz klasörü girin (aşağıda gösterilen *c:\python34\Symbols* gibi *python.pdb'nin* bulunduğu yer) ve Tamam'ı **seçin.**

    ![Karma mod hata ayıklayıcısı sembolleri seçenekleri](media/mixed-mode-debugging-symbols.png)

1. Hata ayıklama oturumu Visual Studio Python yorumlayıcısı için bir kaynak dosyanın konumunu da girmeniz istendiğinde. Kaynak dosyaları indirdiyebilirsiniz [(örneğin python.org/downloads/),](https://www.python.org/downloads/)bunları da işaret ediyor olabilir.

> [!Note]
> İletişim kutusunda gösterilen sembol önbelleğe alma özellikleri, çevrimiçi bir kaynaktan alınan simgelerin yerel önbelleğini oluşturmak için kullanılır. Semboller zaten yerel olarak mevcut olduğu için Python yorumlayıcı sembolleriyle bu özellikler gerekli değildir. Her durumda, ayrıntılar için bkz. Hata [ayıklayıcısında Visual Studio ve](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) kaynak dosyaları belirtme.

## <a name="official-distributions"></a>Resmi dağıtımlar

| Python sürümü | İndirmeler |
| --- | --- |
| 3.5 ve sonrası | Python yükleyicisi aracılığıyla sembolleri yükleyin. |
| 3.4.4 | [32 bit](https://www.python.org/ftp/python/3.4.4/python-3.4.4-pdb.zip)  -  [64 bit](https://www.python.org/ftp/python/3.4.4/python-3.4.4.amd64-pdb.zip) |
| 3.4.3 | [32 bit](https://www.python.org/ftp/python/3.4.3/python-3.4.3-pdb.zip)  -  [64 bit](https://www.python.org/ftp/python/3.4.3/python-3.4.3.amd64-pdb.zip) |
| 3.4.2 | [32 bit](https://www.python.org/ftp/python/3.4.2/python-3.4.2-pdb.zip)  -  [64 bit](https://www.python.org/ftp/python/3.4.2/python-3.4.2.amd64-pdb.zip) |
| 3.4.1 | [32 bit](https://www.python.org/ftp/python/3.4.1/python-3.4.1-pdb.zip)  -  [64 bit](https://www.python.org/ftp/python/3.4.1/python-3.4.1.amd64-pdb.zip) |
| 3.4.0 | [32 bit](https://www.python.org/ftp/python/3.4.0/python-3.4.0-pdb.zip)  -  [64 bit](https://www.python.org/ftp/python/3.4.0/python-3.4.0.amd64-pdb.zip) |
| 3.3.5 | [32 bit](https://www.python.org/ftp/python/3.3.5/python-3.3.5-pdb.zip)  -  [64 bit](https://www.python.org/ftp/python/3.3.5/python-3.3.5.amd64-pdb.zip) |
| 3.3.4 | [32 bit](https://www.python.org/ftp/python/3.3.4/python-3.3.4-pdb.zip)  -  [64 bit](https://www.python.org/ftp/python/3.3.4/python-3.3.4.amd64-pdb.zip) |
| 3.3.3 | [32 bit](https://www.python.org/ftp/python/3.3.3/python-3.3.3-pdb.zip)  -  [64 bit](https://www.python.org/ftp/python/3.3.3/python-3.3.3.amd64-pdb.zip) |
| 3.3.2 | [32 bit](https://www.python.org/ftp/python/3.3.2/python-3.3.2-pdb.zip)  -  [64 bit](https://www.python.org/ftp/python/3.3.2/python-3.3.2.amd64-pdb.zip) |
| 3.3.1 | [32 bit](https://www.python.org/ftp/python/3.3.1/python-3.3.1-pdb.zip)  -  [64 bit](https://www.python.org/ftp/python/3.3.1/python-3.3.1.amd64-pdb.zip) |
| 3.3.0 | [32 bit](https://www.python.org/ftp/python/3.3.0/python-3.3.0-pdb.zip)  -  [64 bit](https://www.python.org/ftp/python/3.3.0/python-3.3.0.amd64-pdb.zip) |
| 2.7.18 | [32 bit](https://www.python.org/ftp/python/2.7.18/python-2.7.18-pdb.zip)  -  [64 bit](https://www.python.org/ftp/python/2.7.18/python-2.7.18.amd64-pdb.zip) |
| 2.7.17 | [32 bit](https://www.python.org/ftp/python/2.7.17/python-2.7.17-pdb.zip)  -  [64 bit](https://www.python.org/ftp/python/2.7.17/python-2.7.17.amd64-pdb.zip) |
| 2.7.16 | [32 bit](https://www.python.org/ftp/python/2.7.16/python-2.7.16-pdb.zip)  -  [64 bit](https://www.python.org/ftp/python/2.7.16/python-2.7.16.amd64-pdb.zip) |
| 2.7.15 | [32 bit](https://www.python.org/ftp/python/2.7.15/python-2.7.15-pdb.zip)  -  [64 bit](https://www.python.org/ftp/python/2.7.15/python-2.7.15.amd64-pdb.zip) |
| 2.7.14 | [32 bit](https://www.python.org/ftp/python/2.7.14/python-2.7.14-pdb.zip)  -  [64 bit](https://www.python.org/ftp/python/2.7.14/python-2.7.14.amd64-pdb.zip) |
| 2.7.13 | [32 bit](https://www.python.org/ftp/python/2.7.13/python-2.7.13-pdb.zip)  -  [64 bit](https://www.python.org/ftp/python/2.7.13/python-2.7.13.amd64-pdb.zip) |
| 2.7.12 | [32 bit](https://www.python.org/ftp/python/2.7.12/python-2.7.12-pdb.zip)  -  [64 bit](https://www.python.org/ftp/python/2.7.12/python-2.7.12.amd64-pdb.zip) |
| 2.7.11 | [32 bit](https://www.python.org/ftp/python/2.7.11/python-2.7.11-pdb.zip)  -  [64 bit](https://www.python.org/ftp/python/2.7.11/python-2.7.11.amd64-pdb.zip) |
| 2.7.10 | [32 bit](https://www.python.org/ftp/python/2.7.10/python-2.7.10-pdb.zip)  -  [64 bit](https://www.python.org/ftp/python/2.7.10/python-2.7.10.amd64-pdb.zip) |
| 2.7.9 | [32 bit](https://www.python.org/ftp/python/2.7.9/python-2.7.9-pdb.zip)  -  [64 bit](https://www.python.org/ftp/python/2.7.9/python-2.7.9.amd64-pdb.zip) |
| 2.7.8 | [32 bit](https://www.python.org/ftp/python/2.7.8/python-2.7.8-pdb.zip)  -  [64 bit](https://www.python.org/ftp/python/2.7.8/python-2.7.8.amd64-pdb.zip) |
| 2.7.7 | [32 bit](https://www.python.org/ftp/python/2.7.7/python-2.7.7-pdb.zip)  -  [64 bit](https://www.python.org/ftp/python/2.7.7/python-2.7.7.amd64-pdb.zip) |
| 2.7.6 | [32 bit](https://www.python.org/ftp/python/2.7.6/python-2.7.6-pdb.zip)  -  [64 bit](https://www.python.org/ftp/python/2.7.6/python-2.7.6.amd64-pdb.zip) |
| 2.7.5 | [32 bit](https://www.python.org/ftp/python/2.7.5/python-2.7.5-pdb.zip)  -  [64 bit](https://www.python.org/ftp/python/2.7.5/python-2.7.5.amd64-pdb.zip) |
| 2.7.4 | [32 bit](https://www.python.org/ftp/python/2.7.4/python-2.7.4-pdb.zip)  -  [64 bit](https://www.python.org/ftp/python/2.7.4/python-2.7.4.amd64-pdb.zip) |
| 2.7.3 | [32 bit](https://www.python.org/ftp/python/2.7.3/python-2.7.3-pdb.zip)  -  [64 bit](https://www.python.org/ftp/python/2.7.3/python-2.7.3.amd64-pdb.zip) |
| 2.7.2 | [32 bit](https://www.python.org/ftp/python/2.7.2/python-2.7.2-pdb.zip)  -  [64 bit](https://www.python.org/ftp/python/2.7.2/python-2.7.2.amd64-pdb.zip) |
| 2.7.1 | [32 bit](https://www.python.org/ftp/python/2.7.1/python-2.7.1-pdb.zip)  -  [64 bit](https://www.python.org/ftp/python/2.7.1/python-2.7.1.amd64-pdb.zip) |

## <a name="enthought-canopy"></a>Canopy 'yi düşündüz

Canopy, 1,2 sürümünden başlayarak ikililerinin sembolleri sağlar. Bunlar, dağıtım ile birlikte otomatik olarak yüklenir, ancak yine de bunları içeren klasörü, daha önce açıklandığı gibi sembol yoluna el ile eklemeniz gerekir. Canopy 'nin tipik Kullanıcı başına yüklemesi için, Semboller 64 bit sürümü için *%USERPROFILE%\appdata\local\enbir Gana* ve 32 bit sürümü için *%USERPROFILE%\appdata\local\enbir Ghght\canopi*

Copy 1,1 ve önceki bir sürümü, Python dağıtımını (EPD), yorumlayıcı sembolleri sağlamayamayın ve bu nedenle karışık modda hata ayıklama ile uyumlu değildir.
