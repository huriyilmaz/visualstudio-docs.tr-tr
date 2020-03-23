---
title: Karışık modpython/C++ hata ayıklama için semboller
description: Visual Studio'nun tam karışık modlu C++ ve Python hata ayıklama için sembolleryükleme olanağı sağlar.
ms.date: 11/12/2018
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- python
- data-science
ms.openlocfilehash: 77dc73b0be050e5108f73d38dfbbaa763d236995
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62957632"
---
# <a name="install-debugging-symbols-for-python-interpreters"></a>Python yorumlayıcıları için hata ayıklama sembolleri yükleme

Tam hata ayıklama deneyimi sağlamak için Visual Studio'daki [karışık modlu Python hata ayıklayıcısının,](debugging-mixed-mode-c-cpp-python-in-visual-studio.md) çok sayıda iç veri yapısını ayrışdırmak için kullanılan Python yorumlayıcısı için hata ayıklama sembollerine ihtiyacı vardır. *Python27.dll*için, örneğin, ilgili sembol dosyası *python27.pdb;* *python36.dll*için, sembol dosyası *python36.pdb*olduğunu. Tercümanın her sürümü de çeşitli modüller için sembol dosyaları sağlar.

Visual Studio 2017 ve sonrası ile Python 3 ve Anaconda 3 tercümanları kendi sembollerini otomatik olarak yükler ve Visual Studio bu sembolleri otomatik olarak bulur. Visual Studio 2015 ve daha önce veya diğer yorumlayıcıları kullanırken, sembolleri ayrı ayrı indirmeniz ve ardından Hata **Ayıklama** > **Sembolleri** sekmesindeki **Araçlar** > **Seçenekleri** iletişim kutusunda Visual Studio'yu onlara doğrultmanız gerekir. Bu adımlar aşağıdaki bölümlerde ayrıntılı olarak açıklanmaktadır.

Visual Studio, genellikle karışık modlu hata ayıklama oturumu başlatırken sembollere ihtiyaç duyduğunda sizi isteyebilir. Bu durumda, iki seçenekiçeren bir iletişim kutusu görüntüler:

- **Sembol ayarlarını aç iletişim kutusu,** **Seçenekler** iletişim kutusunu **Hata Ayıklama** > **Simgeler** sekmesine açar.
- **Tercümanım için indirme sembolleri** bu mevcut belgeler sayfasını açar, bu durumda **Araçlar** > **Seçenekleri'ni** seçin ve devam etmek için **Hata Ayıklama** > **Sembolleri** sekmesine gidin.

    ![Karışık mod hata ayıklama sembolleri istemi](media/mixed-mode-debugging-symbols-required.png)

## <a name="download-symbols"></a>Simgeleri indirin

- Python 3.5 ve sonrası: Python yükleyicisi aracılığıyla hata ayıklama sembolleri edinin. **Özel yükleme**seçin , Gelişmiş **Seçenekler**almak için **Next** seçin, sonra **hata ayıklama sembolleri İndir** ve hata **ayıklama ikilileri indir**için kutuları seçin:

    ![Hata ayıklama sembolleri içeren Python 3.x yükleyici](media/mixed-mode-debugging-symbols-installer35.png)

    Sembol dosyaları (*.pdb*) daha sonra kök yükleme klasöründe bulunur (tek tek modüller için sembol dosyaları da *DLs* klasöründedir). Bu nedenle, Visual Studio bunları otomatik olarak bulur ve başka bir adım alamamaktadır.

- Python 3.4.x ve daha önceki: semboller indirilebilir *.zip* dosyaları [resmi dağıtımları](#official-distributions) veya [Enthought Canopy](#enthought-canopy)olarak kullanılabilir. İndirdikten sonra, Python klasöründeki *Semboller* klasörü gibi devam etmek için dosyaları yerel bir klasöre ayıklayın.

    > [!Important]
    > Semboller Python'un küçük yapıları ile 32 bit ve 64 bit yapılar arasında farklılık gösterir, bu nedenle sürümlerle tam olarak eşleşmek istersiniz. Kullanılan yorumlayıcıyı denetlemek **için, Solution Explorer'da** projenizin altındaki **Python Ortamları** *düğümunu* genişletin ve ortam adını not edin. Ardından Python **Ortamları** *penceresine* geçin ve yükleme konumuna dikkat edin. Ardından, bu konumda bir komut penceresi açın ve tam sürümünü ve 32 bit mi yoksa 64 bit mi olduğunu görüntüleyen *python.exe'yi*başlatın.

- ActiveState Python gibi diğer üçüncü taraf Python dağıtımı için: bu dağıtımın yazarlarıyla iletişime geçin ve size semboller sağlamalarını isteyin. WinPython, kendi payına, değişiklik olmadan standart Python yorumlayıcı içerir, bu nedenle ilgili sürüm numarası için resmi dağıtım sembolleri kullanın.

## <a name="point-visual-studio-to-the-symbols"></a>Sembollere Görsel Stüdyo'yu işaretle

Sembolleri ayrı olarak indirdiyseniz, Visual Studio'nun bu sembollerden haberdar olmasını sağlamak için aşağıdaki adımları izleyin. Sembolleri Python 3.5 veya daha sonraki yükleyiciye yüklediyseniz, Visual Studio bunları otomatik olarak bulur.

1. **Araç** > **Seçenekleri** menüsünü seçin ve **Hata Ayıklama** > **Sembolleri'ne**gidin.

1. Araç çubuğundaki **Ekle** düğmesini (aşağıda özetlenen) seçin, indirilen sembolleri genişlettiğiniz klasörü girin *(python.pdb'nin* bulunduğu yer, aşağıda gösterildiği *c:\python34\Symbols*gibi) ve **Tamam'ı**seçin.

    ![Karışık mod hata ayıklama sembolleri seçenekleri](media/mixed-mode-debugging-symbols.png)

1. Hata ayıklama oturumu sırasında Visual Studio, Python yorumlayıcısı için bir kaynak dosyanın konumunu da isteyebilir. Kaynak dosyaları indirdiyseniz [(örneğin, python.org/downloads/'](https://www.python.org/downloads/)dan) o zaman tabii ki onları da işaret edebilirsiniz.

> [!Note]
> İletişim kutusunda gösterilen simge önbelleğe alma özellikleri, çevrimiçi bir kaynaktan elde edilen simgelerin yerel önbelleği oluşturmak için kullanılır. Semboller zaten yerel olarak mevcut olduğundan, bu özellikler Python yorumlayıcı sembolleri ile gerekli değildir. Her durumda, ayrıntılar için [Visual Studio hata ayıklamasında sembolleri ve kaynak dosyaları](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) belirtin'e bakın.

## <a name="official-distributions"></a>Resmi dağıtımlar

| Python sürümü | İndirmeler |
| --- | --- |
| 3.5 ve sonrası | Python yükleyiciaracılığıyla semboller yükleyin. |
| 3.4.4 | [32 bit](https://www.python.org/ftp/python/3.4.4/python-3.4.4-pdb.zip) - [64 bit](https://www.python.org/ftp/python/3.4.4/python-3.4.4.amd64-pdb.zip) |
| 3.4.3 | [32 bit](https://www.python.org/ftp/python/3.4.3/python-3.4.3-pdb.zip) - [64 bit](https://www.python.org/ftp/python/3.4.3/python-3.4.3.amd64-pdb.zip) |
| 3.4.2 | [32 bit](https://www.python.org/ftp/python/3.4.2/python-3.4.2-pdb.zip) - [64 bit](https://www.python.org/ftp/python/3.4.2/python-3.4.2.amd64-pdb.zip) |
| 3.4.1 | [32 bit](https://www.python.org/ftp/python/3.4.1/python-3.4.1-pdb.zip) - [64 bit](https://www.python.org/ftp/python/3.4.1/python-3.4.1.amd64-pdb.zip) |
| 3.4.0 | [32 bit](https://www.python.org/ftp/python/3.4.0/python-3.4.0-pdb.zip) - [64 bit](https://www.python.org/ftp/python/3.4.0/python-3.4.0.amd64-pdb.zip) |
| 3.3.5 | [32 bit](https://www.python.org/ftp/python/3.3.5/python-3.3.5-pdb.zip) - [64 bit](https://www.python.org/ftp/python/3.3.5/python-3.3.5.amd64-pdb.zip) |
| 3.3.4 | [32 bit](https://www.python.org/ftp/python/3.3.4/python-3.3.4-pdb.zip) - [64 bit](https://www.python.org/ftp/python/3.3.4/python-3.3.4.amd64-pdb.zip) |
| 3.3.3 | [32 bit](https://www.python.org/ftp/python/3.3.3/python-3.3.3-pdb.zip) - [64 bit](https://www.python.org/ftp/python/3.3.3/python-3.3.3.amd64-pdb.zip) |
| 3.3.2 | [32 bit](https://www.python.org/ftp/python/3.3.2/python-3.3.2-pdb.zip) - [64 bit](https://www.python.org/ftp/python/3.3.2/python-3.3.2.amd64-pdb.zip) |
| 3.3.1 | [32 bit](https://www.python.org/ftp/python/3.3.1/python-3.3.1-pdb.zip) - [64 bit](https://www.python.org/ftp/python/3.3.1/python-3.3.1.amd64-pdb.zip) |
| 3.3.0 | [32 bit](https://www.python.org/ftp/python/3.3.0/python-3.3.0-pdb.zip) - [64 bit](https://www.python.org/ftp/python/3.3.0/python-3.3.0.amd64-pdb.zip) |
| 2.7.15 | [32 bit](https://www.python.org/ftp/python/2.7.15/python-2.7.15-pdb.zip) - [64 bit](https://www.python.org/ftp/python/2.7.15/python-2.7.15.amd64-pdb.zip) |
| 2.7.14 | [32 bit](https://www.python.org/ftp/python/2.7.14/python-2.7.14-pdb.zip) - [64 bit](https://www.python.org/ftp/python/2.7.14/python-2.7.14.amd64-pdb.zip) |
| 2.7.13 | [32 bit](https://www.python.org/ftp/python/2.7.13/python-2.7.13-pdb.zip) - [64 bit](https://www.python.org/ftp/python/2.7.13/python-2.7.13.amd64-pdb.zip) |
| 2.7.12 | [32 bit](https://www.python.org/ftp/python/2.7.12/python-2.7.12-pdb.zip) - [64 bit](https://www.python.org/ftp/python/2.7.12/python-2.7.12.amd64-pdb.zip) |
| 2.7.11 | [32 bit](https://www.python.org/ftp/python/2.7.11/python-2.7.11-pdb.zip) - [64 bit](https://www.python.org/ftp/python/2.7.11/python-2.7.11.amd64-pdb.zip) |
| 2.7.10 | [32 bit](https://www.python.org/ftp/python/2.7.10/python-2.7.10-pdb.zip) - [64 bit](https://www.python.org/ftp/python/2.7.10/python-2.7.10.amd64-pdb.zip) |
| 2.7.9 | [32 bit](https://www.python.org/ftp/python/2.7.9/python-2.7.9-pdb.zip) - [64 bit](https://www.python.org/ftp/python/2.7.9/python-2.7.9.amd64-pdb.zip) |
| 2.7.8 | [32 bit](https://www.python.org/ftp/python/2.7.8/python-2.7.8-pdb.zip) - [64 bit](https://www.python.org/ftp/python/2.7.8/python-2.7.8.amd64-pdb.zip) |
| 2.7.7 | [32 bit](https://www.python.org/ftp/python/2.7.7/python-2.7.7-pdb.zip) - [64 bit](https://www.python.org/ftp/python/2.7.7/python-2.7.7.amd64-pdb.zip) |
| 2.7.6 | [32 bit](https://www.python.org/ftp/python/2.7.6/python-2.7.6-pdb.zip) - [64 bit](https://www.python.org/ftp/python/2.7.6/python-2.7.6.amd64-pdb.zip) |
| 2.7.5 | [32 bit](https://www.python.org/ftp/python/2.7.5/python-2.7.5-pdb.zip) - [64 bit](https://www.python.org/ftp/python/2.7.5/python-2.7.5.amd64-pdb.zip) |
| 2.7.4 | [32 bit](https://www.python.org/ftp/python/2.7.4/python-2.7.4-pdb.zip) - [64 bit](https://www.python.org/ftp/python/2.7.4/python-2.7.4.amd64-pdb.zip) |
| 2.7.3 | [32 bit](https://www.python.org/ftp/python/2.7.3/python-2.7.3-pdb.zip) - [64 bit](https://www.python.org/ftp/python/2.7.3/python-2.7.3.amd64-pdb.zip) |
| 2.7.2 | [32 bit](https://www.python.org/ftp/python/2.7.2/python-2.7.2-pdb.zip) - [64 bit](https://www.python.org/ftp/python/2.7.2/python-2.7.2.amd64-pdb.zip) |
| 2.7.1 | [32 bit](https://www.python.org/ftp/python/2.7.1/python-2.7.1-pdb.zip) - [64 bit](https://www.python.org/ftp/python/2.7.1/python-2.7.1.amd64-pdb.zip) |

## <a name="enthought-canopy"></a>Enthought Kanopi

Enthought Canopy, sürüm 1.2'den başlayarak ikili leri için semboller sağlar. Bunlar dağıtımla birlikte otomatik olarak yüklenir, ancak yine de bunları içeren klasörü daha önce açıklandığı gibi sembol yoluna el ile eklemeniz gerekir. Canopy'nin kullanıcı başına tipik bir kurulumu için, semboller % *UserProfile%\AppData\Local\Enthought\Canopy\User\Scripts* for the 64-bit sürümü ve *%UserProfile%\AppData\Local\Enthought\Canopy32\User\Scripts* 32 bit sürüm için bulunur.

Enthought Canopy 1.1 ve daha önceki, yanı sıra Enthought Python Dağıtım (EPD), yorumlayıcı sembolleri sağlamaz ve bu nedenle karışık mod hata ayıklama ile uyumlu değildir.
