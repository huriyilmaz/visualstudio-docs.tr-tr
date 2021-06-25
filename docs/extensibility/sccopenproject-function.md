---
description: Bu işlev var olan bir kaynak denetimi projesini açar veya yeni bir proje oluşturur.
title: SccOpenProject İşlev | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccOpenProject
helpviewer_keywords:
- SccOpenProject function
ms.assetid: d609510b-660a-46d7-b93d-2406df20434d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1326319b483aa707b77e0d7142d816b01fc7d3b1
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902403"
---
# <a name="sccopenproject-function"></a>SccOpenProject İşlevi
Bu işlev var olan bir kaynak denetimi projesini açar veya yeni bir proje oluşturur.

## <a name="syntax"></a>Sözdizimi

```cpp
SCCRTN SccOpenProject (
   LPVOID        pvContext,
   HWND          hWnd,
   LPSTR         lpUser,
   LPCSTR        lpProjName,
   LPCSTR        lpLocalProjPath,
   LPSTR         lpAuxProjPath,
   LPCSTR        lpComment,
   LPTEXTOUTPROC lpTextOutProc,
   LONG          dwFlags
);
```

#### <a name="parameters"></a>Parametreler
 pvContext

[in] Kaynak denetimi eklentisi bağlam yapısı.

 Hwnd

[in] Kaynak denetimi eklentisinin sağladığı iletişim kutuları için üst öğe olarak kullanabileceği IDE penceresi tanıtıcısı.

 lpUser

[in, out] Kullanıcının adı (NULL sonlandırıcı dahil olmak SCC_USER_SIZE aşmama).

 lpProjName

[in] Projenin adını tanımlayan dize.

 lpLocalProjPath

[in] Projenin çalışma klasörünün yolu.

 lpUxProjPath

[in, out] Projeyi tanımlayan isteğe bağlı yardımcı dize (NULL sonlandırıcı dahil SCC_AUXPATH_SIZE aşmama).

 lpComment

[in] Oluşturulan yeni bir projeye açıklama olarak yorum yap.

 lpTextOutProc

[in] Kaynak denetimi eklentisinin metin çıkışını görüntülemek için isteğe bağlı bir geri çağırma işlevi.

 Dwflags

[in] Proje kaynak denetimi eklentisi tarafından bilinmiyorsa yeni bir projenin oluşturulıp oluşturulmay gerektiğini sinyal olarak verir. Değer ve birleşimi `SCC_OP_CREATEIFNEW` olabilir `SCC_OP_SILENTOPEN.`

## <a name="return-value"></a>Dönüş Değeri
 Bu işlevin kaynak denetimi eklentisinin aşağıdaki değerlerden birini dönmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Projeyi açma başarısı.|
|SCC_E_INITIALIZEFAILED|Proje başlatılamadı.|
|SCC_E_INVALIDUSER|Kullanıcı kaynak denetim sisteminde oturum açamdı.|
|SCC_E_COULDNOTCREATEPROJECT|Proje çağrıdan önce mevcut yoktu;  `SCC_OPT_CREATEIFNEW` bayrağı ayarlanmış ancak proje oluşturulamadı.|
|SCC_E_PROJSYNTAXERR|Geçersiz proje söz dizimi.|
|SCC_E_UNKNOWNPROJECT|Proje, kaynak denetimi eklentisi tarafından bilinmiyor ve `SCC_OPT_CREATEIFNEW` bayrağı ayarlanmaz.|
|SCC_E_INVALIDFILEPATH|Geçersiz veya kullanılamaz dosya yolu.|
|SCC_E_NOTAUTHORIZED|Kullanıcının bu işlemi gerçekleştirmesine izin verilmez.|
|SCC_E_ACCESSFAILURE|Büyük olasılıkla ağ veya sorun sorun nedeniyle kaynak denetim sistemine erişilirken bir sorun vardı. Yeniden deneme önerilir.|
|SCC_E_NONSPECFICERROR|Belirtilmeyen bir hata; kaynak denetim sistemi başlatılmadı.|

## <a name="remarks"></a>Açıklamalar
 IDE bir kullanıcı adı ( ) veya `lpUser` boş bir dizenin işaretçisini iletir. Bir kullanıcı adı varsa, kaynak denetimi eklentisi varsayılan olarak kullanmalıdır. Ancak, hiçbir ad geçirilemediyse veya oturum açma işlemi verilen adla başarısız olursa, eklenti kullanıcıdan oturum açmasını ister ve geçerli bir oturum açma aldığında geçerli adı döndürür. Eklenti kullanıcı adı dizesini değiştirebilir çünkü IDE her zaman boyut arabelleği (+1 veya null sonlandırıcı için alan içeren `lpUser` `.` `SCC_USER_LEN` SCC_USER_SIZE) ayırır.

> [!NOTE]
> IDE'nin gerçekleştirmesi gereken ilk eylem, işlevine yapılan bir çağrı veya `SccOpenProject` [SccGetProjPath olabilir.](../extensibility/sccgetprojpath-function.md) Bu nedenle her ikisi de aynı parametreye `lpUser` sahip.

 `lpAuxProjPath``lpProjName`ve çözüm dosyasından okunur veya işlev çağrısından `SccGetProjPath` döndürülür. Bu parametreler, kaynak denetimi eklentisinin projeyle ilişkilendiren dizelerini içerir ve yalnızca eklenti için anlamlıdır. Çözüm dosyasında bu tür dizeler yoksa ve kullanıcıdan göz atması istenmişse (işlev aracılığıyla bir dize döndürür), IDE hem hem de için boş dizeleri iletir ve bu işlev döndürdiğinde bu değerlerin eklenti tarafından güncelleştirilsini `SccGetProjPath` `lpAuxProjPath` `lpProjName` bekler.

 `lpTextOutProc` , IDE tarafından komut sonucu çıktısını görüntüleme amacıyla kaynak denetimi eklentisine sağlanan bir geri çağırma işlevinin işaretçisidir. Bu geri çağırma işlevi [LPTEXTOUTPROC içinde ayrıntılı olarak açıklanmıştır.](../extensibility/lptextoutproc.md)

> [!NOTE]
> Kaynak denetimi eklentisi bundan yararlanmayı hedeflese, `SCC_CAP_TEXTOUT` [SccInitialize içinde bayrağını ayarlamış olması gerekir.](../extensibility/sccinitialize-function.md) Bu bayrak ayarlanmazsa veya IDE bu özelliği desteklemezse `lpTextOutProc` `NULL` olur.

 parametresi, `dwFlags` açılan projenin şu anda mevcut olması durumunda sonucu kontrol eder. İki bit tanesi ve 'den `SCC_OP_CREATEIFNEW` `SCC_OP_SILENTOPEN` oluşur. Açılan proje zaten varsa işlev yalnızca projeyi açar ve `SCC_OK` döndürür. Proje yoksa ve bayrağı açıksa, kaynak denetim eklentisi projeyi kaynak denetim sisteminde oluşturabilir, açabilir ve `SCC_OP_CREATEIFNEW` iade ediyor `SCC_OK` olabilir. Proje yoksa ve bayrak kapalı `SCC_OP_CREATEIFNEW` ise eklenti bayrağını `SCC_OP_SILENTOPEN` denetlemeli. Bu bayrak bağlı değilse, eklenti kullanıcıdan proje adı isteminde olabilir. Bu bayrak varsa eklentinin yalnızca olarak dönmesi `SCC_E_UNKNOWNPROJECT` gerekir.

## <a name="calling-order"></a>Sipariş Çağırma
 Olayların normal kursunda, ilk olarak bir kaynak denetimi oturumu açmak için [SccInitialize](../extensibility/sccinitialize-function.md) çağrılır. Oturum bir çağrısından, ardından diğer Kaynak Denetimi Eklentisi API'si işlev çağrılarını içerir ve `SccOpenProject` [SccCloseProject](../extensibility/scccloseproject-function.md)çağrısıyla sonlandırılır. Bu tür oturumlar [SccUninitialize çağrılmadan önce birkaç kez](../extensibility/sccuninitialize-function.md) yinelenir.

 Kaynak denetimi eklentisi biti içinde `SCC_CAP_REENTRANT` ayarlarsa, yukarıdaki oturum sırası birçok kez `SccInitialize` paralel olarak yinelenir. Farklı `pvContext` yapılar, her birinin aynı anda tek bir açık `pvContext` projeyle ilişkilendirilen farklı oturumları takip ediyor. parametresine `pvContext` bağlı olarak eklenti, belirli bir çağrıda hangi projeye başvurul olduğunu belirler. Yetenek biti ayarlanmazsa, nonreentrant source control eklentileri, birden çok projeyle çalışma `SCC_CAP_REENTRANT` yeteneğinde sınırlıdır.

> [!NOTE]
> Bit, `SCC_CAP_REENTRANT` Kaynak Denetimi Eklentisi API'sini 1.1 sürümünde tanıtıldı. Sürüm 1.0'da ayarlanmaz veya yoksayılır ve tüm sürüm 1.0 kaynak denetimi eklentilerinin nonreentrant olduğu varsayılır.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentisi API İşlevleri](../extensibility/source-control-plug-in-api-functions.md)
- [SccCloseProject](../extensibility/scccloseproject-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [SccUninitialize](../extensibility/sccuninitialize-function.md)
- [Dize Uzunluğu Kısıtlamaları](../extensibility/restrictions-on-string-lengths.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
