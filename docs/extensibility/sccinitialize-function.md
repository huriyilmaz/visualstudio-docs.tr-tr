---
title: SccInitialize Işlevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccInitialize
helpviewer_keywords:
- SccInitialize function
ms.assetid: 5bc0d28b-2c68-4d43-9e51-541506a8f76e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 552ec06a4eabf55872358fc8e5d731e47c1eb6ca
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721179"
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

[in, out] Kaynak denetimi eklentisinin kendi adını (`SCC_NAME_LEN` aşmamak için değil) yerleştirdiğinin arabelleği.

 `lpSccCaps`

dışı Kaynak denetimi eklentisinin yetenek bayraklarını döndürür.

 `lpAuxPathLabel`

[in, out] Kaynak denetimi eklentisinin, [SccOpenProject](../extensibility/sccopenproject-function.md) ve [SccGetProjPath](../extensibility/sccgetprojpath-function.md) tarafından döndürülen `lpAuxProjPath` parametresini açıklayan bir dize koyar (`SCC_AUXLABEL_LEN` aşmamak için değil).

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

 @No__t_0 bir `NULL` işaretçisine işaret eder. Kaynak denetimi eklentisi kendi kullanımı için bir yapı ayırabilir ve bu yapıya bir işaretçi `ppvContext` içinde depolayabilirler. IDE, bu işaretçiyi diğer tüm VSSCI API işlevine geçirerek, eklentinin Genel depolamaya bir daha tekrarsız ve eklentinin birden çok örneğini desteklemesi için bağlam bilgilerinin kullanılabilir olmasını sağlar. [Sccunınitialize](../extensibility/sccuninitialize-function.md) çağrıldığında bu yapının serbest bırakılmaması gerekir.

 @No__t_0 ve `lpSccName` parametreleri, IDE ve kaynak denetimi eklentisini Exchange adları olarak etkinleştirir. Bu adlar yalnızca birden çok örnek arasında ayrım yapmak için veya menüler veya iletişim kutularında görünebilirler.

 @No__t_0 parametresi, çözüm dosyasında depolanan ve [SccOpenProject](../extensibility/sccopenproject-function.md)çağrısı içindeki kaynak denetimi eklentisine geçirilen yardımcı proje yolunu tanımlamak için açıklama olarak kullanılan bir dizedir. [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)], "SourceSafe projesi:" dizesini kullanır. diğer kaynak denetimi eklentileri bu belirli dizeyi kullanmaktan kaçınmalıdır.

 @No__t_0 parametresi, eklentinin yeteneklerini belirten bitflags depolamak için kaynak denetimi eklentisine bir yer verir. (Capability bitflags tam listesi için bkz. [yetenek bayrakları](../extensibility/capability-flags.md)). Örneğin, eklenti, arayan tarafından sağlanmış bir geri çağırma işlevine sonuçları yazacaksa, eklenti, capability bit SCC_CAP_TEXTOUT olarak ayarlanır. Bu, IDE 'nin sürüm denetimi sonuçları için bir pencere oluşturmasını işaret edecektir.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentisi API İşlevleri](../extensibility/source-control-plug-in-api-functions.md)
- [SccUninitialize](../extensibility/sccuninitialize-function.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [Özellik Bayrakları](../extensibility/capability-flags.md)