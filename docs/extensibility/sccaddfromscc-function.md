---
title: SccAddFromScc Fonksiyonu | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccAddFromScc
helpviewer_keywords:
- SccAddFromScc function
ms.assetid: 902e764d-200e-46e1-8c42-4da7b037f9a0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1dd32e31330cdce958e463a40a4d92f88b09afb2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701241"
---
# <a name="sccaddfromscc-function"></a>SccAddFromScc fonksiyonu
Bu işlev, kullanıcının kaynak denetim sisteminde zaten bulunan dosyalara göz atmasına ve daha sonra bu dosyaları geçerli projenin bir parçası haline getirmesine olanak tanır. Örneğin, bu işlev, dosyayı kopyalamadan geçerli projeye ortak bir üstbilgi dosyası alabilir. Dosyaların iade dizisi, `lplpFileNames`kullanıcının IDE projesine eklemek istediği dosyaların listesini içerir.

## <a name="syntax"></a>Sözdizimi

```cpp
SCCRTN SccAddFromScc (
   LPVOID   pvContext,
   HWND     hWnd,
   LPLONG   lpnFiles,
   LPCSTR** lplpFileNames
);
```

### <a name="parameters"></a>Parametreler
 pvContext

[içinde] Kaynak denetimi eklentisi bağlam yapısı.

 Hwnd

[içinde] Kaynak denetim eklentisinin sağladığı tüm iletişim kutuları için üst öğe olarak kullanabileceği IDE penceresine bir tanıtıcı.

 lpnFiles

[içinde, dışarı] Eklenen dosya sayısı için bir arabellek. (Bu `NULL` bellek tarafından `lplpFileNames` işaret serbest bırakılacak ise. Ayrıntılar için Açıklamalar'a bakın.)

 lplpFileNames

[içinde, dışarı] Dizin yolları olmayan tüm dosya adlarına işaretçiler dizisi. Bu dizi, kaynak denetim eklentisi tarafından ayrılır ve serbest bırakılır. `lpnFiles` = 1 `lplpFileNames` ve `NULL`değilse , hedef klasörü `lplpFileNames` içeren dizideki ilk ad.

## <a name="return-value"></a>Dönüş Değeri
 Bu işlevin kaynak denetim eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Dosyalar başarıyla konumlandı ve projeye eklendi.|
|SCC_I_OPERATIONCANCELED|İşlem hiçbir şekilde iptal edildi.|
|SCC_I_RELOADFILE|Bir dosyanın veya projenin yeniden yüklenmesi gerekir.|

## <a name="remarks"></a>Açıklamalar
 IDE bu işlevi çağırır. Kaynak denetimi eklentisi yerel bir hedef klasörbelirtmeyi destekliyorsa, IDE = 1'den geçer `lpnFiles` ve yerel klasör adını `lplpFileNames`.

 İşlev çağrısı geri döndüğünde, eklenti, dosya adı `lpnFiles` `lplpFileNames`dizisi için belleği gerektiği gibi ayırarak değerler atamıştır (bu `lplpFileNames`ayırmanın işaretçinin yerini aldığından not edin). `SccAddFromScc` Kaynak denetimi eklentisi, tüm dosyaları kullanıcının dizinine veya belirtilen atama klasörüne yerleştirmekten sorumludur. IDE daha sonra dosyaları IDE projesine ekler.

 Son olarak, IDE bu işlevi ikinci `NULL` kez `lpnFiles`çağırır, için geçen. Bu, dosya adı dizisi için ayrılan belleği serbest bırakmak için kaynak denetim eklentisi tarafından özel bir sinyal olarak yorumlanır`lplpFileNames``.`

 `lplpFileNames`bir `char ***` işaretçidir. Kaynak denetimi eklentisi, bir işaretçiyi dosya adları için bir dizi işaretçiye yerleştirir ve böylece listeyi bu API için standart şekilde geçer.

> [!NOTE]
> VSSCI API'nin ilk sürümleri, eklenen dosyalar için hedef projeyi göstermek için bir yol sağlamadı. Bunu karşılamak için, `lplpFIleNames` parametrenin semantik bir çıkış parametresi yerine bir in/out parametresi yapmak için geliştirilmiştir. Yalnızca tek bir dosya belirtilirse, yani `lpnFiles` = 1'in işaret ettiği `lplpFileNames` değer, hedef klasörü içerir. Bu yeni semantik leri kullanmak için, `SccSetOption` IDE `nOption`parametre `SCC_OPT_SHARESUBPROJ`olarak ayarlanmış işlevi çağırır. Kaynak denetim eklentisi semantikleri desteklemiyorsa, `SCC_E_OPTNOTSUPPORTED`döndürür. Bunu yapmak, **Kaynak Denetimi'nden Ekle** özelliğinin kullanımını devre dışı kılabilir. Bir eklenti **Kaynak Denetiminden Ekle** özelliğini`SCC_CAP_ADDFROMSCC`destekliyorsa ( ), yeni semantikleri desteklemesi ve döndürmesi `SCC_I_SHARESUBPROJOK`gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak kontrol eklentisi API fonksiyonları](../extensibility/source-control-plug-in-api-functions.md)
- [SccSetOption](../extensibility/sccsetoption-function.md)
