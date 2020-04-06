---
title: SccInitialize Fonksiyonu | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccInitialize
helpviewer_keywords:
- SccInitialize function
ms.assetid: 5bc0d28b-2c68-4d43-9e51-541506a8f76e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 661e0a24fa1d222079fd5ee728c5f42a5386c75b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700639"
---
# <a name="sccinitialize-function"></a>SccInitialize İşlevi
Bu işlev, kaynak denetim eklentisini başolarak inceler ve tümleşik geliştirme ortamına (IDE) yetenek ve sınırlar sağlar.

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

[içinde] Kaynak denetim eklentisi, bir işaretçini bağlam yapısına buraya yerleyebilir.

 `hWnd`

[içinde] Kaynak denetim eklentisinin sağladığı tüm iletişim kutuları için üst öğe olarak kullanabileceği IDE penceresine bir tanıtıcı.

 `lpCallerName`

[içinde] Kaynak denetim eklentisini çağıran programın adı.

 `lpSccName`

[içinde, dışarı] Kaynak denetim eklentisinin kendi adını koyduğu arabellek (aşmayacak). `SCC_NAME_LEN`

 `lpSccCaps`

[çıkış] Kaynak denetimi eklentisinin yetenek bayraklarını döndürür.

 `lpAuxPathLabel`

[içinde, dışarı] Kaynak denetim eklentisinin [sccOpenProject](../extensibility/sccopenproject-function.md) ve [SccGetProjPath](../extensibility/sccgetprojpath-function.md) tarafından döndürülen `SCC_AUXLABEL_LEN` `lpAuxProjPath` parametreyi açıklayan bir dize koyduğu arabellek (aşmayacak).

 `pnCheckoutCommentLen`

[çıkış] Ödeme açıklaması için izin verilen maksimum uzunluğu verir.

 `pnCommentLen`

[çıkış] Diğer yorumlar için izin verilen maksimum uzunluğu verir.

## <a name="return-value"></a>Dönüş Değeri
 Bu işlevin kaynak denetim eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Kaynak denetimi başlatma başarılı oldu.|
|SCC_E_INITIALIZEFAILED|Sistem başharfe bıyıltılamadı.|
|SCC_E_NOTAUTHORIZED|Kullanıcının belirtilen işlemi gerçekleştirmesine izin verilmez.|
|SCC_E_NONSPECFICERROR|Nonspesifik başarısızlık; kaynak kontrol sistemi başharfe bürünmedi.|

## <a name="remarks"></a>Açıklamalar
 IDE, kaynak denetim eklentisini ilk yüklendiğinde bu işlevi çağırır. IDE'nin arayan adı gibi belirli bilgileri eklentiye aktarmasını sağlar. IDE ayrıca, yorumlar için izin verilen maksimum uzunluk ve eklentinin yetenekleri gibi belirli bilgileri de geri alır.

 Bir `ppvContext` `NULL` işaretçiye işaret eden noktalar. Kaynak denetim eklentisi bir yapıyı kendi kullanımı için ayırabilir ve `ppvContext`bu yapıya bir işaretçi depolayabilir. IDE bu işaretçiyi diğer tüm VSSCI API işlevine geçirerek eklentinin genel depolamaya başvurmadan bağlam bilgilerinin kullanılabilir olmasını ve eklentinin birden çok örneğini desteklemesine olanak sağlar. [SccUninitialize](../extensibility/sccuninitialize-function.md) çağrıldığında bu yapı ayrılır.

 Ve `lpCallerName` `lpSccName` parametreler IDE ve kaynak denetim eklentisi adlarını değiştirmek için etkinleştirin. Bu adlar yalnızca birden çok örnek arasında ayrım yapmak için kullanılabilir veya menülerde veya iletişim kutularında görünebilir.

 Parametre, `lpAuxPathLabel` çözüm dosyasında depolanan ve [SccOpenProject'e](../extensibility/sccopenproject-function.md)yapılan bir çağrıda kaynak denetim eklentisine geçirilen yardımcı proje yolunu tanımlamak için yorum olarak kullanılan bir dizedir. [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)]dizesini kullanır "SourceSafe Project:"; diğer kaynak denetim eklentileri bu özel dizeyi kullanmaktan kaçınmalıdır.

 Parametre, `lpSccCaps` kaynak denetimi eklentisine eklentinin fişin yeteneklerini gösteren bit bayraklarını depolamak için bir yer verir. (Yetenek bit bayraklarının tam listesi için [Yetenek Bayrakları'na](../extensibility/capability-flags.md)bakın). Örneğin, eklenti, arayan tarafından sağlanan geri arama işlevine sonuç yazmayı planlıyorsa, eklenti yetenek bitini SCC_CAP_TEXTOUT ayarlar. Bu, sürüm denetim sonuçları için bir pencere oluşturmak için IDE sinyali verir.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentisi API İşlevleri](../extensibility/source-control-plug-in-api-functions.md)
- [SccUninitialize](../extensibility/sccuninitialize-function.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [Özellik Bayrakları](../extensibility/capability-flags.md)
