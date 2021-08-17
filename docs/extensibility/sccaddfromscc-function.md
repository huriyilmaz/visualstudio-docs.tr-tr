---
description: Bu işlev, kullanıcının kaynak denetim sisteminde zaten olan dosyalara göz atarak bu dosyaları geçerli projenin parçası yapmalarına olanak sağlar.
title: SccAddFromScc İşlevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccAddFromScc
helpviewer_keywords:
- SccAddFromScc function
ms.assetid: 902e764d-200e-46e1-8c42-4da7b037f9a0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 888a0e0647fe84861f430c31449e86944a7193bfe7cc56583a35f273849d431d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121388167"
---
# <a name="sccaddfromscc-function"></a>SccAddFromScc işlevi
Bu işlev, kullanıcının kaynak denetim sisteminde zaten olan dosyalara göz atarak bu dosyaları geçerli projenin parçası yapmalarına olanak sağlar. Örneğin, bu işlev dosyayı kopyalamadan geçerli projeye ortak bir üst bilgi dosyası elde ediyor olabilir. Dosya dönüş dizisi olan `lplpFileNames` , kullanıcının IDE projesine eklemek istediği dosyaların listesini içerir.

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

[in] Kaynak denetimi eklentisi bağlam yapısı.

 Hwnd

[in] Kaynak denetimi eklentisinin sağladığı iletişim kutuları için üst öğe olarak kullanabileceği IDE penceresi tanıtıcısı.

 lpnFiles

[in, out] Eklenen dosya sayısı için bir arabellek. (Bu, `NULL` tarafından işaret eden belleğin serbest `lplpFileNames` bırakılama olmasıdır. Ayrıntılar için bkz. Açıklamalar.)

 lplpFileNames

[in, out] Dizin yolları olmayan tüm dosya adlarının işaretçileri dizisi. Bu dizi, kaynak denetimi eklentisi tarafından ayrılır ve serbest bıraktır. `lpnFiles`= 1 ise `lplpFileNames` ve `NULL` değilse, tarafından işaret eden dizideki ad `lplpFileNames` hedef klasörü içerir.

## <a name="return-value"></a>Dönüş Değeri
 Bu işlevin kaynak denetimi eklentisinin aşağıdaki değerlerden birini geri dönmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Dosyalar başarıyla bulundu ve projeye eklendi.|
|SCC_I_OPERATIONCANCELED|İşlem hiçbir etkiyle iptal edildi.|
|SCC_I_RELOADFILE|Bir dosyanın veya projenin yeniden yüklenmiş olması gerekir.|

## <a name="remarks"></a>Açıklamalar
 IDE bu işlevi çağıran bir işlevdir. Kaynak denetimi eklentisi yerel hedef klasör belirtmeyi destekliyorsa, IDE = 1'i geçer ve yerel `lpnFiles` klasör adını içine `lplpFileNames` iletir.

 İşleve yapılan çağrı döndür geldiğinde eklenti ve değerlerine atadığı için dosya adı dizisi için gerekli belleği ayırması gerekir (bu ayırmanın dosyasındaki işaretçinin yerini `SccAddFromScc` `lpnFiles` `lplpFileNames` `lplpFileNames` alır). Kaynak denetimi eklentisi, tüm dosyaları kullanıcının dizinine veya belirtilen atama klasörüne yerleştirmekle sorumludur. Ardından IDE dosyaları IDE projesine ekler.

 Son olarak, IDE bu işlevi ikinci kez çağırarak için `NULL` `lpnFiles` iletir. Bu, içinde dosya adı dizisi için ayrılan belleği serbest bırakmak için kaynak denetimi eklentisi tarafından özel bir sinyal olarak yorumlanır `lplpFileNames``.`

 `lplpFileNames` bir `char ***` işaretçidir. Kaynak denetimi eklentisi, dosya adlarında işaretçi dizisine bir işaretçi yererek listeyi bu API için standart şekilde geçirmenizi sağlar.

> [!NOTE]
> VSSCI API'nin ilk sürümleri, eklenen dosyalar için hedef projeyi belirtmek için bir yol sağlamadı. Bunu karşılamak için parametrenin semantiği, çıkış parametresi yerine `lplpFIleNames` bir giriş/çıkış parametresi olacak şekilde geliştirilmiştir. Yalnızca tek bir dosya belirtilirse, yani tarafından işaret eden değer = 1 ise, öğesinin ilk `lpnFiles` `lplpFileNames` öğesi hedef klasörü içerir. Bu yeni semantiği kullanmak için, IDE parametresi olarak `SccSetOption` ayarlanmış `nOption` şekilde işlevini `SCC_OPT_SHARESUBPROJ` çağırtır. Kaynak denetimi eklentisi semantiği desteklemezse `SCC_E_OPTNOTSUPPORTED` döndürür. Bunu yapmak Kaynak Denetiminden Ekle **özelliğinin kullanımını devre dışı** bırakıyor. Bir eklenti Kaynak Denetiminden **Ekle özelliğini** () destekliyorsa, yeni semantiği desteklemesi ve ' yi `SCC_CAP_ADDFROMSCC` desteklemesi `SCC_I_SHARESUBPROJOK` gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak denetimi eklentisi API işlevleri](../extensibility/source-control-plug-in-api-functions.md)
- [SccSetOption](../extensibility/sccsetoption-function.md)
