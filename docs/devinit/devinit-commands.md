---
title: devinit komutları
description: Bileşenleri yüklemek için devinit komutlarının nasıl kullanılacağına ilişkin ayrıntılar.
ms.date: 08/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: d6c8f487fcb35fc210db57f0c8a49a2a86f909e9
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672216"
---
# <a name="devinit-commands"></a>devinit komutları

> [!IMPORTANT]
> 12 Nisan 2021 itibariyle, Visual Studio 2019 ' den GitHub Codespaces 'a bağlanmak artık desteklenmeyecektir ve bu özel önizleme sona ermiştir. Bulut destekli bir iç döngü ve çok sayıda Visual Studio iş yükü için iyileştirilmiş VDı çözümleri için gelişen deneyimlere odaklanıyoruz. Bu `devinit` ve ilişkili araçların bir parçası olarak artık kullanılabilir olmayacaktır. Gelecekteki önizlemeler ve yol haritası bilgileri hakkında bilgi için, Visual Studio için geliştirici topluluğu forumumuza dahil etmeniz önerilir.

## <a name="init"></a>Init

```console
devinit init
```

Dosyasında [.devinit.js](devinit-json.md) belirtilen araçları çalıştırarak ortamı başlatın.

### <a name="options-for-init"></a>İnit seçenekleri

Komut için isteğe bağlı seçenekler `devinit init` .

| Bağımsız Değişken             | Gerekli | Açıklama                                                               |
|----------------------|----------|---------------------------------------------------------------------------|
| -f,--dosyası            | No       | `.devinit.json`Dosyanın yolu.                                         |
| --hata-eylem       | No       | Hataların nasıl işleneceğini belirtir. Seçenekler: durdur, Yoksay, devam et (varsayılan).|
| -v,--verbose         | No       | Ayrıntılı çıktıyı yay.                                                      |
| -n,--Kuru çalıştırma         | No       | Kuru çalıştırma.                                                                  |

#### <a name="--file-argument"></a>--Dosya bağımsız değişkeni

Dosyadaki _devinit.js_ yolunu belirtir. --Dosyası belirtilmemişse, aşağıdaki konumlarda varsayılan bir dosya aradık:

* {geçerli-dizin} \\ Üzerinde.devinit.js
* {geçerli-dizin} \\ Üzerindedevinit.js
* {geçerli-dizin} \\ . devinit \\.devinit.json
* {geçerli-dizin} \\ . devinit \\devinit.json
* {geçerli-dizin} \\ devinit \\.devinit.json
* {geçerli-dizin} \\ devinit \\devinit.json
* {geçerli-dizin} \\ . devcontainer \\.devinit.json
* {geçerli-dizin} \\ . devcontainer \\devinit.json

> [!NOTE]
> Birden çok varsayılan dosya bulunursa, devınit yukarıdaki listede ilk görüntülenen dosyayı kullanır.

#### <a name="--error-action-argument"></a>--hata-eylem bağımsız değişkeni

[Aşağıya](#options-for-run)bakın.

#### <a name="--verbose-switch"></a>--ayrıntılı anahtar

[Aşağıya](#options-for-run)bakın.

#### <a name="--dry-run-switch"></a>--Kuru çalıştırma anahtarı

[Aşağıya](#options-for-run)bakın.

## <a name="run"></a>Çalıştır

```console
devinit run -t <toolname>
```

Belirli aracı çalıştırır, parametreler aşağıda listelenmiştir. Belirli kullanımlar için her bir araç için [belgelere](devinit-tool-list.md) bakın.

### <a name="options-for-run"></a>Çalıştırma seçenekleri

Komut için Seçenekler `devinit run` .

| Bağımsız Değişken                                      | Gerekli | Açıklama                                                                          |
|-----------------------------------------------|----------|--------------------------------------------------------------------------------------|
| -t,--aracı                                     | Yes      | Gereklidir. Araç adı.                                                             |
| -ı,--girişi                                    | No       | Araç giriş değeri. Örneğin, bir dosya adı, paket veya ad.                     |
| --hata-eylem                                | No       | Araç hatalarının nasıl işleneceğini belirtir: durdur, Yoksay, devam et. Varsayılan değer durdurulur. |
| -v,--verbose                                  | No       | Ayrıntılı çıktıyı yay.                                                                 |
| -n,--Kuru çalıştırma                                  | No       | Kuru çalıştırma.                                                                             |
| --&lt;arg1 &gt; &lt; arg2 &gt; ... &lt; argN&gt;  | No       | Araca ek komut satırı bağımsız değişkenleri.                                       |

#### <a name="--error-action-argument"></a>--hata-eylem bağımsız değişkeni

Bir araç sıfır olmayan bir çıkış kodu döndürürse gerçekleştirilecek eylemi belirtir. Geçerli değerler şunlardır:

| Bağımsız Değişken | Description                                                                                                                                                                                                                                                                           |
|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| continue | Standart hataya bir hata gönderdikten sonra diğer araçları işlemeye devam edin. devinit.exe çıkış kodu sıfır değil (hata). Bu davranış durdurma hatası eylemine benzerdir, ancak işleme devam eder. `continue` init komutu için varsayılan hata-eylem.              |
| yoksayma   | Standart çıktıya bir uyarı yaydıktan sonra diğer araçları işlemeye devam edin. DevInit işlem çıkış kodu her zaman sıfır (başarılı) olmalıdır. `ignore`Ayar tüm hataları yoksayar.                                                                                                      |
| Dur     | Standart hataya bir hata yayar ve araçları işlemeyi durduruyor. devinit.exe çıkış kodu sıfır değil (hata). Bu, devam etme hatası eylemine benzerdir, ancak karşılaşılan ilk hatada işleme durdurulur. `stop` , init hariç tüm komutlar için varsayılan hata eylemi olur. |

#### <a name="--dry-run-switch"></a>--Kuru çalıştırma anahtarı

Çalıştırılacak yankı aracı komutları. Bazı araçlar, söz konusu araç için belgelendiği şekilde daha fazla işlem gerçekleştirebilir. 

#### <a name="--verbose-switch"></a>--ayrıntılı anahtar

Ayrıntılı çıktıyı standart çıktıya yay. Yürütülecek araç ayrıntılı bir seçeneği destekliyorsa, ayrıntılı anahtarı araca yayın.

#### <a name="--dry-run-switch"></a>--Kuru çalıştırma anahtarı

Çalıştırılacak, ancak herhangi bir araç yürütmeyin yankı araç komutları.

#### <a name="additional-command-line-arguments"></a>Ek komut satırı bağımsız değişkenleri

Değerinde bir boşluk içeren bir kullanmak, başka bir kaçış `<arg>` tırnak çifti içermelidir.

```console
devinit run -t <toolname> -<somearg> "<some value>"
```

Belirli bir dizine DotNet yüklemek için `C:\Program Files\dotnet` :

```console
devinit run -t require-dotnetcoresdk --"-InstallDir \"C:\Program Files\dotnet\""
```

## <a name="list"></a>Liste

```console
devinit list
```

Tüm kullanılabilir araçların listesini yazdırır.

## <a name="show"></a>Göster

```console
devinit show -t <toolname>
```

| Bağımsız Değişken       | Gerekli | Açıklama                                                                          |
|----------------|----------|--------------------------------------------------------------------------------------|
| -t,--aracı      | Yes      | Gereklidir. Araç adı.                                                             |

Belirli bir araç için yardım bilgilerini yazdırır.

## <a name="version"></a>Sürüm

```console
devinit version
```

Devinit için geçerli sürüm bilgilerini yazdırır.

## <a name="help"></a>Help

```console
devinit help
devinit help list
```

Devinit veya belirli bir komut için yardım metnini yazdırır `devinit <command>` .
 
