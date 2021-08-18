---
description: Bu işlev, görüntülemek ve derlemek için bir veya daha fazla dosyanın kopyasını alır ancak düzenleme için almaz.
title: SccGet İşlev | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccGet
helpviewer_keywords:
- SccGet function
ms.assetid: 09a18bd2-b788-411a-9da6-067d806e46f6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 0c2b3927da5b7d59100a31e9c347d4f32e2118e3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122049525"
---
# <a name="sccget-function"></a>SccGet işlevi
Bu işlev, görüntülemek ve derlemek için bir veya daha fazla dosyanın kopyasını alır ancak düzenleme için almaz. Çoğu sistemde dosyalar salt okunur olarak etiketlenir.

## <a name="syntax"></a>Sözdizimi

```cpp
SCCRTN SccGet(
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>Parametreler
 pvContext

[in] Kaynak denetimi eklentisinin bağlam yapısı.

 Hwnd

[in] Kaynak denetimi eklentisinin sağladığı iletişim kutuları için üst öğe olarak kullanabileceği IDE penceresi tanıtıcısı.

 nFiles

[in] Dizide belirtilen dosya `lpFileNames` sayısı.

 lpFileNames

[in] Alınecek dosyaların tam adları dizisi.

 fOptions

[in] Komut bayrakları ( `SCC_GET_ALL` , `SCC_GET_RECURSIVE` ).

 pvOptions

[in] Kaynak denetimi eklentisine özgü seçenekler.

## <a name="return-value"></a>Döndürülen değer
 Bu işlevin kaynak denetimi eklentisinin aşağıdaki değerlerden birini geri dönmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|get işlemi başarıyla.|
|SCC_E_FILENOTCONTROLLED|Dosya kaynak denetimi altında değil.|
|SCC_E_OPNOTSUPPORTED|Kaynak denetim sistemi bu işlemi desteklemez.|
|SCC_E_FILEISCHECKEDOUT|Kullanıcının kullanıma alınmış olduğu dosya bulunamıyor.|
|SCC_E_ACCESSFAILURE|Kaynak denetim sistemine erişirken büyük olasılıkla ağ veya iletişim sorunları nedeniyle bir sorun vardı. Yeniden deneme önerilir.|
|SCC_E_NOSPECIFIEDVERSION|Geçersiz bir sürüm veya tarih/saat belirtildi.|
|SCC_E_NONSPECIFICERROR|Belirtilmeyen hata; dosyası eşitlenmedi.|
|SCC_I_OPERATIONCANCELED|İşlem tamamlanmadan önce iptal edildi.|
|SCC_E_NOTAUTHORIZED|Kullanıcının bu işlemi gerçekleştirme yetkisi yok.|

## <a name="remarks"></a>Açıklamalar
 Bu işlev, alınmak için bir sayı ve bir dizi ad ile çağrılır. IDE bayrağını geçerse, bu, 'daki öğelerin dosya değil dizin olduğu ve verilen dizinlerde kaynak denetimi altındaki tüm dosyaların alın anlamına `SCC_GET_ALL` `lpFileNames` gelir.

 Bayrağı, verilen dizinlerde ve tüm alt dizinlerde yer alan tüm dosyaları almak `SCC_GET_ALL` `SCC_GET_RECURSIVE` için bayrağıyla birlikte kullanılabilir.

> [!NOTE]
> `SCC_GET_RECURSIVE`hiçbir zaman olmadan geçirilene kadar. `SCC_GET_ALL` Ayrıca, *C:\A* ve *C:\A\B* dizinleri bir yinelemeli get üzerinde geçirilmişse, *C:\A\B* dizinleri ve tüm alt dizinleri aslında iki kez alınır. Bunun gibi yinelenenlerin dizi dışında tutulması, IDE'nin sorumluluğundadır (kaynak denetim eklentisinin değil).

 Son olarak, bir kaynak denetimi eklentisi başlatma sırasında bayrağını belirtse bile, Get komutu için bir kullanıcı arabirimi olmadığını belirtse bile, bu işlev dosyaları almak için IDE tarafından `SCC_CAP_GET_NOUI` çağrılabilse bile. Bayrağı basitçe IDE'nin bir Get menü öğesini görüntülemeyeceği ve eklentinin herhangi bir kullanıcı arabirimi sağlamayı bekleneceği anlamına gelir.

## <a name="rename-files-and-sccget"></a>Dosyaları yeniden adlandırma ve SccGet
 Durum: Kullanıcı, bir dosyayı (örneğin, *a.txt)* denetler ve bu dosyayı denetler. Bir *a.txt* önce, ikinci bir kullanıcı *a.txt'ı* kaynak denetim veritabanında *b.txt* olarak yeniden adlandırır, *b.txt'ı* kullanıma alır, dosyada bazı değişiklikler yapar ve dosyayı denetler. İlk kullanıcı, ikinci kullanıcı tarafından yapılan değişiklikleri ister, bu nedenle ilk kullanıcı *a.txt* yerel sürümünü yeniden adlandırarakb.txtdosya üzerinde bir get yapar.  Ancak, sürüm numaralarının takip landığı yerel önbellek, a.txtyerel olarak depolandığı için kaynak denetimi farkları çözemezse de ilk sürümün depolandığına karar verir.

 Kaynak denetimi sürümlerinin yerel önbelleğinin kaynak denetim veritabanıyla eşitnin dışında olduğu bu durumu çözmenin iki yolu vardır:

1. Kaynak denetim veritabanında o anda kullanıma alınmış bir dosyanın yeniden adı olmasına izin verme.

2. "Eski silme" ve ardından "yeni ekle" eşdeğerini yapar. Bunu gerçekleştirmenin bir yolu aşağıdaki algoritmadır.

    1. Kaynak denetimi veritabanındaki veri kaynağına yenidena.txthakkında *bilgib.txt* [SccQueryChanges](../extensibility/sccquerychanges-function.md) işlevini çağırma. 

    2. Yerel dosyanın *adınıa.txt* olarak *b.txt.*

    3. hem `SccGet` hem de a.txtiçin *işlevinib.txt.*

    4. Kaynak *a.txt* veritabanında mevcut olmadığınız için, yerel sürüm önbelleği eksik sürüm *a.txt* temiz olur.

    5. Kullanıma *b.txt* dosya yerel dosyanın içeriğiyle *b.txt.*

    6. Güncelleştirilmiş *b.txt* dosyası artık iade olabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak denetimi eklentisi API işlevleri](../extensibility/source-control-plug-in-api-functions.md)
- [Belirli komutlar tarafından kullanılan bit bayrakları](../extensibility/bitflags-used-by-specific-commands.md)
