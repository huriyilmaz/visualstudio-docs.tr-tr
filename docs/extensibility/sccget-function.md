---
title: SccGet Fonksiyonu | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGet
helpviewer_keywords:
- SccGet function
ms.assetid: 09a18bd2-b788-411a-9da6-067d806e46f6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c2d69308d2f569fc2e0d72dcf64c762687955d4d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700898"
---
# <a name="sccget-function"></a>SccGet fonksiyonu
Bu işlev, görüntülemek ve derlemek için bir veya daha fazla dosyanın kopyasını alır, ancak düzenleme için değil. Çoğu sistemde, dosyalar salt okunur olarak etiketlenir.

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

[içinde] Kaynak denetim eklentisinin bağlam yapısı.

 Hwnd

[içinde] Kaynak denetim eklentisinin sağladığı tüm iletişim kutuları için üst öğe olarak kullanabileceği IDE penceresine bir tanıtıcı.

 nDosyalar

[içinde] `lpFileNames` Dizide belirtilen dosya sayısı.

 lpFileNames

[içinde] Alınacak dosyaların tam nitelikli adlarını dizi.

 fSeçenekler

[içinde] Komut bayrakları`SCC_GET_ALL` `SCC_GET_RECURSIVE`( , ).

 pvOptions

[içinde] Kaynak denetimi eklentisi özel seçenekleri.

## <a name="return-value"></a>Döndürülen değer
 Bu işlevin kaynak denetim eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Ameliyat alma başarısı.|
|SCC_E_FILENOTCONTROLLED|Dosya kaynak denetimi altında değil.|
|SCC_E_OPNOTSUPPORTED|Kaynak denetim sistemi bu işlemi desteklemez.|
|SCC_E_FILEISCHECKEDOUT|Kullanıcının şu anda kullanıma yaptırdığı dosyayı alamıyor.|
|SCC_E_ACCESSFAILURE|Kaynak denetim sistemine erişmede büyük olasılıkla ağ veya çekişme sorunları nedeniyle bir sorun vardı. Yeniden deneme önerilir.|
|SCC_E_NOSPECIFIEDVERSION|Geçersiz bir sürüm veya tarih/saat belirtilmiş.|
|SCC_E_NONSPECIFICERROR|Nonspesifik başarısızlık; dosya eşitlenmedi.|
|SCC_I_OPERATIONCANCELED|İşlem tamamlanmadan iptal edildi.|
|SCC_E_NOTAUTHORIZED|Kullanıcının bu işlemi gerçekleştirme yetkisi yoktur.|

## <a name="remarks"></a>Açıklamalar
 Bu işlev, bir sayım ve alınacak dosyaların adlarının bir dizi ile çağrılır. IDE bayrağı `SCC_GET_ALL`geçerse, bu, içeri ye `lpFileNames` gelen öğelerin dosya değil dizinler olduğu ve verilen dizinlerde kaynak denetimi altındaki tüm dosyaların alınıp alınacayacak anlamına gelir.

 Bayrak, `SCC_GET_ALL` verilen dizinler ve tüm alt dizinler deki tüm dosyaları almak için `SCC_GET_RECURSIVE` bayrakla birleştirilebilir.

> [!NOTE]
> `SCC_GET_RECURSIVE`olmadan `SCC_GET_ALL`asla geçilmemelidir. Ayrıca, *C:\A* ve *C:\A\B* dizinlerinin her ikisi de özyinelemeli bir get'e geçerse, *C:\A\B* ve tüm alt dizinlerinin aslında iki kez alınacağını unutmayın. Bu gibi yinelemelerin dizinin dışında tutulduğundan emin olmak, kaynak denetim eklentisinin değil, IDE'nin sorumluluğudur.

 Son olarak, bir kaynak denetim eklentisi başlatma da `SCC_CAP_GET_NOUI` bayrağı belirtmiş olsa bile, Get komutu için bir kullanıcı arabirimi olmadığını belirterek, bu işlev yine de Dosyaları almak için IDE tarafından çağrılabilir. Bayrak basitçe, IDE'nin Get menü öğesini görüntülemediği ve eklentinin herhangi bir UI sağlamasının beklenmediği anlamına gelir.

## <a name="rename-files-and-sccget"></a>Dosyaları yeniden adlandırın ve SccGet
 Durum: Bir kullanıcı bir dosyayı, örneğin, *a.txt'yi*denetler ve onu değiştirir. *a.txt* iade edilmeden önce, ikinci bir kullanıcı kaynak denetim veritabanında *a.txt'yi* *b.txt* olarak yeniden adlandırır, *b.txt'yi*kontrol eder, dosyada bazı değişiklikler yapar ve dosyayı iade eder. İlk kullanıcı ikinci kullanıcı tarafından yapılan değişiklikleri istiyor, böylece ilk kullanıcı *a.txt* dosyasının yerel sürümünü *b.txt* olarak yeniden adlandırır ve dosyaya bir şey alır. Ancak, sürüm numaralarını izleyen yerel önbellek hala *a.txt'nin* ilk sürümünün yerel olarak depolanır ve bu nedenle kaynak denetiminin farklılıkları çözemeyeceğini düşünür.

 Kaynak denetimi sürümlerinin yerel önbelleğinin kaynak denetim veritabanıyla eşitlenerek gerçekleştiği bu durumu çözmenin iki yolu vardır:

1. Şu anda kullanıma alınmakta olan kaynak denetim veritabanında bir dosyanın yeniden adlandırılmasına izin vermeyin.

2. "Eskisi sil" ve ardından "yeni ekle" eşdeğerini yapın. Aşağıdaki algoritma bunu başarmanın bir yoludur.

    1. Kaynak denetim veritabanında *a.txt'nin* *b.txt'ye* yeniden adlandırılması hakkında bilgi edinmek için [SccQueryChanges](../extensibility/sccquerychanges-function.md) işlevini arayın.

    2. Yerel *a.txt'yi* *b.txt*olarak yeniden adlandırın.

    3. Hem *a.txt* hem de *b.txt*işlevini arayın. `SccGet`

    4. kaynak denetim veritabanında *a.txt* olmadığından, yerel sürüm önbelleği eksik *a.txt* sürüm bilgilerinden arındırılır.

    5. Kullanıma alınan *b.txt* dosyası yerel *b.txt* dosyasının içeriğiyle birleştirilir.

    6. Güncelleştirilmiş *b.txt* dosyası artık iade edilebilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak kontrol eklentisi API fonksiyonları](../extensibility/source-control-plug-in-api-functions.md)
- [Belirli komutlar tarafından kullanılan Bit bayrakları](../extensibility/bitflags-used-by-specific-commands.md)
