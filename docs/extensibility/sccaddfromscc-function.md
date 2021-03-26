---
description: Bu işlev, kullanıcının zaten kaynak denetimi sisteminde bulunan dosyalara gözatmasını ve ardından bu dosyaları geçerli projenin bir parçası yapmasını sağlar.
title: SccAddFromScc Işlevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccAddFromScc
helpviewer_keywords:
- SccAddFromScc function
ms.assetid: 902e764d-200e-46e1-8c42-4da7b037f9a0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: be67fd18c6cac7217da0d79aaef766e942e15fb9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085682"
---
# <a name="sccaddfromscc-function"></a>SccAddFromScc işlevi
Bu işlev, kullanıcının zaten kaynak denetimi sisteminde bulunan dosyalara gözatmasını ve ardından bu dosyaları geçerli projenin bir parçası yapmasını sağlar. Örneğin, bu işlev, geçerli projeye dosyayı kopyalamadan ortak bir üst bilgi dosyası alabilir. Dosyaların dönüş dizisi, `lplpFileNames` kullanıcının IDE projesine eklemek istediği dosyaların listesini içerir.

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

'ndaki Kaynak denetimi eklentisi bağlam yapısı.

 lendiği

'ndaki Kaynak denetimi eklentisinin, sağladığı tüm iletişim kutuları için üst öğe olarak kullanabileceği IDE penceresi için bir işleyici.

 lpnFiles

[in, out] İçine eklenmekte olan dosya sayısı için bir arabellek. (Bu, `NULL` tarafından işaret edilen belleğin `lplpFileNames` yayımlanacaksa olur. Ayrıntılar için bkz. açıklamalar.)

 Lplpdosyaadı

[in, out] Dizin yolları olmayan tüm dosya adlarına işaretçiler dizisi. Bu dizi, kaynak denetimi eklentisi tarafından ayrılır ve serbest bırakılır. `lpnFiles`= 1 ise ve belirtilmemişse `lplpFileNames` `NULL` dizideki ilk ad `lplpFileNames` hedef klasörü içerir.

## <a name="return-value"></a>Dönüş Değeri
 Bu işlevin kaynak denetimi eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Dosyalar başarıyla bulundu ve projeye eklendi.|
|SCC_I_OPERATIONCANCELED|İşlem, hiçbir etkisi olmadan iptal edildi.|
|SCC_I_RELOADFILE|Bir dosya veya projenin yeniden yüklenmesi gerekiyor.|

## <a name="remarks"></a>Açıklamalar
 IDE bu işlevi çağırır. Kaynak denetimi eklentisi yerel bir hedef klasör belirtmeyi destekliyorsa, IDE = 1 ' i geçirir `lpnFiles` ve yerel klasör adını ' ye geçirir `lplpFileNames` .

 İşlev çağrısı döndürüldüğünde `SccAddFromScc` , eklenti ve için değerler atanır `lpnFiles` ve `lplpFileNames` dosya adı dizisinin belleğini gerektiği şekilde ayırarak (Bu ayırmanın içindeki işaretçinin yerini aldığını unutmayın `lplpFileNames` ). Kaynak denetimi eklentisi, tüm dosyaları kullanıcının dizinine veya belirtilen atama klasörüne yerleştirmekten sorumludur. Daha sonra IDE, dosyaları IDE projesine ekler.

 Son olarak, IDE bu işlevi ikinci bir kez çağırır, için öğesine `NULL` geçer `lpnFiles` . Bu, içindeki dosya adı dizisine ayrılan belleği serbest bırakmak için kaynak denetimi eklentisi tarafından özel bir sinyal olarak yorumlanır. `lplpFileNames``.`

 `lplpFileNames` bir `char ***` işaretçidir. Kaynak denetimi eklentisi dosya adlarına işaretçiler dizisine bir işaretçi koyar, bu nedenle listeyi bu API için standart şekilde geçirerek.

> [!NOTE]
> VSSCI API 'sinin ilk sürümleri, eklenen dosyalar için hedef projeyi göstermek için bir yol sağlamadı. Buna uyum sağlamak için, parametresinin semantiği bir `lplpFIleNames` çıkış parametresi yerine bir ın/out parametresi haline getirmek üzere geliştirilmiştir. Yalnızca tek bir dosya belirtilmişse, diğer bir deyişle, = 1 ile işaret edilen değer, `lpnFiles` sonra da ilk öğesi `lplpFileNames` hedef klasörü içerir. Bu yeni semantiğini kullanmak için IDE, `SccSetOption` `nOption` parametresi olarak ayarlanan parametresini çağırır `SCC_OPT_SHARESUBPROJ` . Bir kaynak denetimi eklentisi semantiğini desteklemiyorsa, döndürür `SCC_E_OPTNOTSUPPORTED` . Bunun yapılması, **kaynak denetimi Ekle** özelliğinin kullanımını devre dışı bırakır. Bir eklenti **kaynak denetiminden Ekle** özelliğini ( `SCC_CAP_ADDFROMSCC` ) destekliyorsa, yeni semantiğini ve dönmesini desteklemelidir `SCC_I_SHARESUBPROJOK` .

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak denetimi eklentisi API işlevleri](../extensibility/source-control-plug-in-api-functions.md)
- [SccSetOption](../extensibility/sccsetoption-function.md)
