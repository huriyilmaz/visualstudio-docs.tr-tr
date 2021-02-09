---
title: SccInitialize Işlevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccInitialize
helpviewer_keywords:
- SccInitialize function
ms.assetid: 5bc0d28b-2c68-4d43-9e51-541506a8f76e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d9fb944cb672249ecb823f48048d12c1b61d9e99
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99846367"
---
# <a name="sccinitialize-function"></a>SccInitialize İşlevi
Bu işlev, kaynak denetimi eklentisini başlatır ve tümleşik geliştirme ortamı (IDE) için özellik ve sınırlar sağlar.

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

'ndaki Kaynak denetimi eklentisi, onun bağlam yapısına bir işaretçi yerleştirebilir.

 `hWnd`

'ndaki Kaynak denetimi eklentisinin, sağladığı tüm iletişim kutuları için üst öğe olarak kullanabileceği IDE penceresi için bir işleyici.

 `lpCallerName`

'ndaki Kaynak denetimi eklentisini çağıran programın adı.

 `lpSccName`

[in, out] Kaynak denetimi eklentisinin kendi adını (aşmamak için değil) yerleştirdiğinin buffer `SCC_NAME_LEN` .

 `lpSccCaps`

dışı Kaynak denetimi eklentisinin yetenek bayraklarını döndürür.

 `lpAuxPathLabel`

[in, out] Kaynak denetimi eklentisinin, `lpAuxProjPath` [SccOpenProject](../extensibility/sccopenproject-function.md) ve [SccGetProjPath](../extensibility/sccgetprojpath-function.md) (aşmamak için) tarafından döndürülen parametreyi açıklayan bir dize koyar `SCC_AUXLABEL_LEN` .

 `pnCheckoutCommentLen`

dışı Kullanıma alma yorumu için izin verilen en yüksek uzunluğu döndürür.

 `pnCommentLen`

dışı Diğer açıklamalar için izin verilen en fazla uzunluğu döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Bu işlevin kaynak denetimi eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Kaynak denetimi başlatması başarılı oldu.|
|SCC_E_INITIALIZEFAILED|Sistem başlatılamadı.|
|SCC_E_NOTAUTHORIZED|Kullanıcının belirtilen işlemi gerçekleştirmesine izin verilmiyor.|
|SCC_E_NONSPECFICERROR|Özel olmayan hata; kaynak denetim sistemi başlatılmadı.|

## <a name="remarks"></a>Açıklamalar
 IDE, kaynak denetimi eklentisini ilk kez yüklediğinde bu işlevi çağırır. IDE 'nin arayan adı gibi belirli bilgileri eklentiye geçmesini sağlar. IDE, açıklamalar için izin verilen en fazla uzunluk ve eklentinin özellikleri gibi belirli bilgileri de geri alır.

 `ppvContext`Bir işaretçiye işaret eder `NULL` . Kaynak denetimi eklentisi kendi kullanımı için bir yapı ayırabilir ve içindeki bu yapıya bir işaretçi depolayabilirler `ppvContext` . IDE, bu işaretçiyi diğer tüm VSSCI API işlevine geçirerek, eklentinin Genel depolamaya bir daha tekrarsız ve eklentinin birden çok örneğini desteklemesi için bağlam bilgilerinin kullanılabilir olmasını sağlar. [Sccunınitialize](../extensibility/sccuninitialize-function.md) çağrıldığında bu yapının serbest bırakılmaması gerekir.

 `lpCallerName`Ve `lpSccName` PARAMETRELERI, IDE ve kaynak denetimi eklentisini Exchange adları olarak etkinleştirir. Bu adlar yalnızca birden çok örnek arasında ayrım yapmak için veya menüler veya iletişim kutularında görünebilirler.

 `lpAuxPathLabel`Parametresi, çözüm dosyasında depolanan ve [SccOpenProject](../extensibility/sccopenproject-function.md)çağrısı içindeki kaynak denetimi eklentisine geçirilen yardımcı proje yolunu tanımlamak için açıklama olarak kullanılan bir dizedir. [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] "SourceSafe projesi:" dizesini kullanır. diğer kaynak denetimi eklentileri bu belirli dizeyi kullanmaktan kaçınmalıdır.

 `lpSccCaps`Parametresi, eklentinin yeteneklerini belirten bitflags depolamak için kaynak denetimi eklentisine sahip bir yer sağlar. (Capability bitflags tam listesi için bkz. [yetenek bayrakları](../extensibility/capability-flags.md)). Örneğin, eklenti çağrı tarafından sağlanmış bir geri çağırma işlevine sonuçları yazacaksa, eklenti, yetenek bit SCC_CAP_TEXTOUT ayarlar. Bu, IDE 'nin sürüm denetimi sonuçları için bir pencere oluşturmasını işaret edecektir.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentisi API İşlevleri](../extensibility/source-control-plug-in-api-functions.md)
- [SccUninitialize](../extensibility/sccuninitialize-function.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [Özellik Bayrakları](../extensibility/capability-flags.md)
