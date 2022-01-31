---
title: Karışık mod Python/C++ hata ayıklama sembolleri
description: Visual Studio, tam karışık mod C++ ve Python hata ayıklama için sembolleri yükleme yeteneği sağlar.
ms.date: 01/27/2022
ms.topic: how-to
author: rjmolyneaux
ms.author: rmolyneaux
manager: jmartens
ms.technology: vs-python
ms.workload:
- python
- data-science
ms.openlocfilehash: 4f2c32f8d58a161c8e8152af61a4f4c6d259b0d7
ms.sourcegitcommit: 20f9529648e69707063dccb2b15089bf4e9bf639
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/31/2022
ms.locfileid: "137887040"
---
# <a name="install-debugging-symbols-for-python-interpreters"></a>Python yorumlayıcıları için hata ayıklama sembolleri yükler

tam bir hata ayıklama deneyimi sağlamak için Visual Studio içindeki [karma mod Python hata ayıklayıcısı](debugging-mixed-mode-c-cpp-python-in-visual-studio.md) , çok sayıda iç veri yapısını ayrıştırmak için kullanılan Python yorumlayıcısı için hata ayıklama sembollerine ihtiyaç duyuyor. Örneğin, *python27.dll* için, karşılık gelen sembol dosyası *python27. pdb*; *python36.dll* için, sembol dosyası *python36. pdb*' dir. Yorumlayıcı 'nın her sürümü, çeşitli modüller için sembol dosyaları da sağlar.

Visual Studio 2017 ve sonrasında Python 3 ve anaconda 3 yorumlayıcıları ilgili sembolleri otomatik olarak yükler ve Visual Studio bu sembolleri otomatik olarak bulur. Visual Studio 2015 ve önceki sürümlerde veya diğer yorumlayıcıları kullanırken, sembolleri ayrı olarak indirmeniz ve sonra **hata ayıklama**  >  **sembolleri** sekmesindeki **araçlar**  >  **seçenekleri** iletişim kutusunda Visual Studio işaret etmeniz gerekir. Bu adımlar aşağıdaki bölümlerde ayrıntılı olarak verilmiştir.

Visual Studio, genellikle karışık modda bir hata ayıklama oturumu başlatırken semboller gerektiğinde size sorabilir. Bu durumda, iki seçenekten oluşan bir iletişim kutusu görüntülenir:

- **Sembol ayarlarını Aç iletişim kutusu** , **hata ayıklama**  >  **sembolleri** sekmesindeki **Seçenekler** iletişim kutusunu açar.
- **Yorumlayıcı için sembolleri indir** bu mevcut belge sayfasını açar, bu durumda **Araçlar**  >  **Seçenekler** ' i seçin ve devam etmek için **hata ayıklama**  >  **sembolleri** sekmesine gidin.

    ![Karışık mod hata ayıklayıcısı sembolleri istemi](media/mixed-mode-debugging-symbols-required.png)

## <a name="download-symbols"></a>Sembolleri indir

- Python 3,5 ve üzeri: Python yükleyicisi aracılığıyla hata ayıklama sembolleri alın. **Özel yükleme**' yi seçin, **İleri** ' yi seçerek **Gelişmiş seçeneklere** ulaşın ve **hata ayıklama sembollerini indir** ve **hata ayıklama ikililerini indir**' i seçin:

    ![Hata ayıklama sembolleri dahil Python 3. x yükleyicisi](media/mixed-mode-debugging-symbols-installer35.png)

    Sembol dosyaları (*. pdb*) daha sonra kök yükleme klasöründe bulunur (ayrı modüller için sembol dosyaları da *DLL* klasöründedir). bu nedenle, Visual Studio onları otomatik olarak bulur ve başka bir adım gerekmez.

- Python 3.4. x ve önceki sürümler: semboller, [resmi dağıtımlarından](#official-distributions) indirilebilir *.zip* dosyaları olarak kullanılabilir ve [Canopy olarak düşünülebilir](#enthought-canopy). İndirdikten sonra, Python klasörü içindeki *semboller* klasörü gibi devam etmek için dosyaları yerel bir klasöre ayıklayın.

    > [!Important]
    > Semboller, Python 'un küçük derlemeleri ve 32-bit ve 64 bit derlemeler arasında farklılık gösterir, bu nedenle sürümleri tam olarak eşleştirmek istersiniz. Kullanılan yorumlayıcı 'yı denetlemek için **Çözüm Gezgini** ' de projenizin altındaki **Python ortamları** *düğümünü* genişletin ve ortam adını aklınızda yapın. Daha sonra **Python ortamları** *penceresine* geçin ve yüklemenin konumunu aklınızda yapın. Ardından, bu konumda bir komut penceresi açın ve *python.exe* başlatın, bu sürüm tam sürümü ve 32 bit mi yoksa 64 bit mi olduğunu gösterir.

- ActiveState Python gibi diğer üçüncü taraf Python dağıtımı için: Bu dağıtımın yazarlarıyla iletişim kurun ve size sembolleri sağlamak üzere isteyin. WinPython, bölümü için standart Python yorumlayıcı 'yı değişiklik yapmadan birleştirir, bu nedenle söz konusu sürüm numarası için resmi dağılıcınızdan sembolleri kullanın.

## <a name="point-visual-studio-to-the-symbols"></a>simgelere Visual Studio nokta

sembolleri ayrı olarak indirdiyseniz, Visual Studio farkında olmak için aşağıdaki adımları izleyin. sembolleri Python 3,5 veya sonraki bir yükleyici aracılığıyla yüklediyseniz Visual Studio onları otomatik olarak bulur.

1. **Araç**  >  **seçenekleri** menüsünü seçin ve **hata ayıklama**  >  **sembolleri**' ne gidin.

1. Araç çubuğunda **Ekle** düğmesini (aşağıda özetlenmiştir) seçin, indirilen sembolleri genişletmiş olduğunuz klasörü (aşağıda gösterildiği *gibi,* *Python. pdb* 'Nin bulunduğu yer) girin ve **Tamam**' ı seçin.

    ![Karışık mod hata ayıklayıcısı sembolleri seçenekleri](media/mixed-mode-debugging-symbols.png)

1. bir hata ayıklama oturumu sırasında, Visual Studio Python yorumlayıcı için bir kaynak dosyasının konumunu da isteyebilir. Kaynak dosyaları (örneğin, [Python.org/downloads/](https://www.python.org/downloads/)adresinden) indirdiyseniz kurs da bunlara işaret edebilir.

> [!Note]
> İletişim kutusunda gösterilen sembol önbelleğe alma özellikleri, çevrimiçi bir kaynaktan alınan bir sembol yerel önbelleği oluşturmak için kullanılır. Semboller zaten yerel olarak mevcut olduğundan, bu özellikler Python yorumlayıcı sembollerinde gerekli değildir. herhangi bir durumda, ayrıntılar için [Visual Studio hata ayıklayıcısında sembolleri ve kaynak dosyaları belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) bölümüne bakın.

## <a name="official-distributions"></a>Resmi dağıtımlar

| Python sürümü | İndirmeler |
| --- | --- |
| 3,5 ve üzeri | Python yükleyicisi aracılığıyla sembolleri yükleme. |
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
| 2.7.11 'i özelleştirme | [32 bit](https://www.python.org/ftp/python/2.7.11/python-2.7.11-pdb.zip)  -  [64 bit](https://www.python.org/ftp/python/2.7.11/python-2.7.11.amd64-pdb.zip) |
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
