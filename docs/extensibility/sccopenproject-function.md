---
title: SccOpenProject Fonksiyonu | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccOpenProject
helpviewer_keywords:
- SccOpenProject function
ms.assetid: d609510b-660a-46d7-b93d-2406df20434d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fbf566e593bb1ddbc31c70de1570d746a14fbdcf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700566"
---
# <a name="sccopenproject-function"></a>SccOpenProject İşlevi
Bu işlev varolan bir kaynak denetim projesini açar veya yeni bir tane oluşturur.

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

[içinde] Kaynak denetimi eklentisi bağlam yapısı.

 Hwnd

[içinde] Kaynak denetim eklentisinin sağladığı tüm iletişim kutuları için üst öğe olarak kullanabileceği IDE penceresine bir tanıtıcı.

 lpUser

[içinde, dışarı] Kullanıcının adı (NULL sonlandırıcı dahil olmak üzere SCC_USER_SIZE geçmemelidir).

 lpProjName

[içinde] Projenin adını tanımlayan dize.

 lpLocalProjPath

[içinde] Proje için çalışma klasörüne giden yol.

 lpAuxProjPath

[içinde, dışarı] Projeyi tanımlayan isteğe bağlı yardımcı dize (NULL sonlandırıcı dahil SCC_AUXPATH_SIZE geçmemek üzere).

 lpYorum yap

[içinde] Oluşturulmakta olan yeni bir projeye yorum yapın.

 lpTextOutProc

[içinde] Kaynak denetimi eklentisinden metin çıktısını görüntülemek için isteğe bağlı bir geri arama işlevi.

 Dwflags

[içinde] Proje kaynak denetim eklentisi tarafından bilinmiyorsa yeni bir projenin oluşturulması gerekip gerekmediğini bildirir. Değer bir arada `SCC_OP_CREATEIFNEW` olabilir ve`SCC_OP_SILENTOPEN.`

## <a name="return-value"></a>Dönüş Değeri
 Bu işlevin kaynak denetim eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Projenin açılışında başarı.|
|SCC_E_INITIALIZEFAILED|Proje başharfe alınamadı.|
|SCC_E_INVALIDUSER|Kullanıcı kaynak denetim sistemine giriş yapamadı.|
|SCC_E_COULDNOTCREATEPROJECT|Proje çağrıdan önce yoktu;  `SCC_OPT_CREATEIFNEW` bayrak ayarlandı, ancak proje oluşturulamadı.|
|SCC_E_PROJSYNTAXERR|Geçersiz proje sözdizimi.|
|SCC_E_UNKNOWNPROJECT|Proje kaynak denetim eklentisi tarafından bilinmiyor `SCC_OPT_CREATEIFNEW` ve bayrak ayarlanmadı.|
|SCC_E_INVALIDFILEPATH|Geçersiz veya kullanılamaz dosya yolu.|
|SCC_E_NOTAUTHORIZED|Kullanıcının bu işlemi gerçekleştirmesine izin verilmez.|
|SCC_E_ACCESSFAILURE|Kaynak denetim sistemine erişmede büyük olasılıkla ağ veya çekişme sorunları nedeniyle bir sorun vardı. Yeniden deneme önerilir.|
|SCC_E_NONSPECFICERROR|Nonspesifik bir hata; kaynak kontrol sistemi başharfe bürünmedi.|

## <a name="remarks"></a>Açıklamalar
 IDE bir kullanıcı adı (),`lpUser`veya sadece boş bir dize için bir işaretçi geçebilir geçebilir. Bir kullanıcı adı varsa, kaynak denetim eklentisi varsayılan olarak kullanmalıdır. Ancak, hiçbir ad geçirilirse veya oturum açma verilen adla başarısız olduysa, eklenti kullanıcıdan oturum açmasını `lpUser` ister ve geçerli`.` bir giriş aldığında geçerli adı döndürür çünkü eklenti kullanıcı adı dizesini`SCC_USER_LEN`değiştirebilir, IDE her zaman bir boyut arabelleği (+1 veya SCC_USER_SIZE, null terminator için boşluk içerir).

> [!NOTE]
> IDE gerçekleştirmek için gerekli olabilir ilk eylem `SccOpenProject` işlevi veya [SccGetProjPath](../extensibility/sccgetprojpath-function.md)bir çağrı olabilir. Bu nedenle, her ikisi de `lpUser` aynı parametreye sahiptir.

 `lpAuxProjPath`ve`lpProjName` çözüm dosyasından okunur veya bir çağrıdan işleve `SccGetProjPath` döndürülür. Bu parametreler, kaynak denetimi eklentisinin projeyle ilişkilendirdiyi ve yalnızca eklenti için anlamlı olan dizeleri içerir. Çözüm dosyasında bu tür dizeler yoksa ve kullanıcıdan göz atması istenmemişse `SccGetProjPath` (işlev boyunca bir dize döndürür), IDE hem de , boş `lpAuxProjPath` `lpProjName`dizeleri geçirir ve bu işlev döndüğünde bu değerlerin eklenti tarafından güncelleştirilmelerini bekler.

 `lpTextOutProc`komut sonucu çıktısını görüntülemek amacıyla Kaynak denetim eklentisine IDE tarafından sağlanan bir geri arama işleviiçin bir işaretçidir. Bu geri arama işlevi [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)ayrıntılı olarak açıklanmıştır.

> [!NOTE]
> Kaynak denetim eklentisi bundan yararlanmak istiyorsa, `SCC_CAP_TEXTOUT` [SccInitialize'deki](../extensibility/sccinitialize-function.md)bayrağı ayarlamış olmalıdır. Bu bayrak ayarlanmadıysa veya IDE bu özelliği `lpTextOutProc` desteklemiyorsa, `NULL`.

 Parametre, `dwFlags` açılan projenin şu anda mevcut olmaması durumunda sonucu denetler. Bu iki bit bayrakları `SCC_OP_CREATEIFNEW` `SCC_OP_SILENTOPEN`oluşur ve . Açılan proje zaten varsa, işlev yalnızca projeyi `SCC_OK`açar ve döndürür. Proje yoksa ve `SCC_OP_CREATEIFNEW` bayrak açıksa, kaynak denetim eklentisi projeyi kaynak denetim sisteminde oluşturabilir, açabilir `SCC_OK`ve döndürebilir. Proje yoksa ve `SCC_OP_CREATEIFNEW` bayrak kapalıysa, eklenti nin bayrağı denetlemesi `SCC_OP_SILENTOPEN` gerekir. Bu bayrak üzerinde değilse, eklenti kullanıcıdan bir proje adı isteyebilir. Bu bayrak üzerindeyse, eklenti basitçe geri `SCC_E_UNKNOWNPROJECT`dönmelidir.

## <a name="calling-order"></a>Arama Siparişi
 Olayların normal seyrinde, [SccInitialize](../extensibility/sccinitialize-function.md) bir kaynak denetim oturumu açmak için ilk çağrılır. Bir `SccOpenProject`oturum, diğer Kaynak Denetimi Eklentisi API işlevi çağrıları nın ardından gelen bir çağrıdan oluşabilir ve [SccCloseProject'e](../extensibility/scccloseproject-function.md)yapılan bir çağrıyla sonlandırır. Bu tür [oturumlar, SccUninitialize](../extensibility/sccuninitialize-function.md) çağrılmadan önce birkaç kez tekrarlanabilir.

 Kaynak denetim eklentisi biti `SCC_CAP_REENTRANT` `SccInitialize`ayarlarsa, yukarıdaki oturum sırası paralel olarak birçok kez yinelenebilir. Farklı `pvContext` yapılar, her birinin `pvContext` aynı anda bir açık projeyle ilişkilendirildiği farklı oturumları izler. Parametreye`pvContext` bağlı olarak, eklenti belirli bir çağrıda hangi projeye başvurulabileceğini belirleyebilir. Yetenek biti `SCC_CAP_REENTRANT` ayarlanmazsa, reentrant olmayan kaynak denetimi eklentileri birden çok projeyle çalışma yetenekleri sınırlıdır.

> [!NOTE]
> Bit, `SCC_CAP_REENTRANT` Kaynak Denetimi Eklentisi API'sinin 1.1 sürümünde tanıtıldı. Sürüm 1.0'da ayarlanmaz veya yoksayılır ve tüm sürüm 1.0 kaynak denetim eklentilerinin reentrant olmadığı varsayılır.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentisi API İşlevleri](../extensibility/source-control-plug-in-api-functions.md)
- [SccCloseProject](../extensibility/scccloseproject-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [SccUninitialize](../extensibility/sccuninitialize-function.md)
- [Dize Uzunluğu Kısıtlamaları](../extensibility/restrictions-on-string-lengths.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
