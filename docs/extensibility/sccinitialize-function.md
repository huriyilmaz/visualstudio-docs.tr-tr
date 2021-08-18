---
description: Bu işlev kaynak denetimi eklentiyi başlatarak tümleşik geliştirme ortamına (IDE) özellikler ve sınırlar sağlar.
title: SccInitialize İşlevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccInitialize
helpviewer_keywords:
- SccInitialize function
ms.assetid: 5bc0d28b-2c68-4d43-9e51-541506a8f76e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: ef0d2cc678bc32d33aa8fec0fdfbea4ee9a619bd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122110221"
---
# <a name="sccinitialize-function"></a>SccInitialize İşlevi
Bu işlev kaynak denetimi eklentiyi başlatarak tümleşik geliştirme ortamına (IDE) özellikler ve sınırlar sağlar.

## <a name="syntax"></a>Sözdizimi

```cpp
SCCRTN SccInitialize (
   LPVOID* ppvContext,
   HWND    hWnd,
   LPCSTR  lpCallerName,
   LPSTR   lpSccName,
   LPLONG  lpSccCaps,
   LPSTR   lpAuxPathLabel,
   LPLONG  pnCheckoutCommentLen,
   LPLONG  pnCommentLen
);
```

#### <a name="parameters"></a>Parametreler
 `ppvContext`

[in] Kaynak denetimi eklentisi, bağlam yapısına bir işaretçiyi buraya yer ettirebilirsiniz.

 `hWnd`

[in] Kaynak denetimi eklentisinin sağladığı iletişim kutuları için üst öğe olarak kullanabileceği IDE penceresi tanıtıcısı.

 `lpCallerName`

[in] Kaynak denetimi eklentiyi çağıran programın adı.

 `lpSccName`

[in, out] Kaynak denetimi eklentisinin kendi adını (aşmamalıdır) koyacağı `SCC_NAME_LEN` arabellek.

 `lpSccCaps`

[out] Kaynak denetimi eklentisinin yetenek bayraklarını döndürür.

 `lpAuxPathLabel`

[in, out] Kaynak denetimi eklentisinin `lpAuxProjPath` [SccOpenProject ve SccGetProjPath](../extensibility/sccopenproject-function.md) tarafından döndürülen parametreyi açıklayan bir dize koyacağı arabellek [](../extensibility/sccgetprojpath-function.md) (aşmamalıdır). `SCC_AUXLABEL_LEN`

 `pnCheckoutCommentLen`

[out] Bir iade açıklaması için izin verilen maksimum uzunluğu döndürür.

 `pnCommentLen`

[out] Diğer açıklamalar için izin verilen maksimum uzunluğu döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Bu işlevin kaynak denetimi eklentisinin aşağıdaki değerlerden birini geri dönmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Kaynak denetimi başlatma başarılı oldu.|
|SCC_E_INITIALIZEFAILED|Sistem başlatılamadı.|
|SCC_E_NOTAUTHORIZED|Kullanıcının belirtilen işlemi gerçekleştirmesine izin verilmez.|
|SCC_E_NONSPECFICERROR|Belirtilmeyen hata; kaynak denetim sistemi başlatılmadı.|

## <a name="remarks"></a>Açıklamalar
 IDE, kaynak denetimi eklentiyi ilk kez yüklerken bu işlevi çağırmaktadır. IDE'nin eklentiye çağıran adı gibi belirli bilgileri iletsine olanak sağlar. IDE ayrıca açıklamalar için izin verilen maksimum uzunluk ve eklentinin özellikleri gibi belirli bilgileri de geri alır.

 bir `ppvContext` işaretçiye `NULL` işaret ediyor. Kaynak denetimi eklentisi, kendi kullanımı için bir yapı ayırarak içinde bu yapıya bir işaretçi `ppvContext` depolar. IDE bu işaretçiyi diğer tüm VSSCI API işlevine iletir ve eklentinin genel depolamaya başvurmadan ve eklentinin birden çok örneğini desteklemeden bağlam bilgilerine sahip olmasına olanak sağlar. [SccUninitialize çağrıldı olduğunda bu yapının atması](../extensibility/sccuninitialize-function.md) gerekir.

 ve `lpCallerName` `lpSccName` parametreleri, ad değişimi için IDE'yi ve kaynak denetimi eklentiyi etkinleştirir. Bu adlar yalnızca birden çok örnek arasında ayrım yapmak için kullanılabilir veya menülerde veya iletişim kutularında görünebilir.

 parametresi, çözüm dosyasında depolanan ve `lpAuxPathLabel` [SccOpenProject](../extensibility/sccopenproject-function.md)çağrısında kaynak denetimi eklentisine geçirilen yardımcı proje yolunu tanımlamak için açıklama olarak kullanılan bir dizedir. [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)]"SourceSafe Project:" dizesini kullanır; diğer kaynak denetimi eklentileri bu dizeyi kullanmamalıdır.

 parametresi, kaynak denetimi eklentisine eklentinin özelliklerini gösteren bit bayraklarını `lpSccCaps` depolayacak bir yer sağlar. (Yetenek bit bayraklarının tam listesi için bkz. [Yetenek Bayrakları](../extensibility/capability-flags.md)). Örneğin, eklenti sonuçları çağıran tarafından sağlanan bir geri çağırma işlevine yazmayı planlıyorsa, eklenti bit özelliğini SCC_CAP_TEXTOUT. Bu, IDE'ye sürüm denetimi sonuçları için bir pencere oluşturması sinyali verir.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentisi API İşlevleri](../extensibility/source-control-plug-in-api-functions.md)
- [SccUninitialize](../extensibility/sccuninitialize-function.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [Özellik Bayrakları](../extensibility/capability-flags.md)
