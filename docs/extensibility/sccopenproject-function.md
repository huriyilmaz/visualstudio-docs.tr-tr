---
title: SccOpenProject Işlevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccOpenProject
helpviewer_keywords:
- SccOpenProject function
ms.assetid: d609510b-660a-46d7-b93d-2406df20434d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a6aa4a715f8d1b87aa831f6a315f07a19e5d4f46
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721050"
---
# <a name="sccopenproject-function"></a>SccOpenProject İşlevi
Bu işlev, var olan bir kaynak denetimi projesini açar veya yeni bir tane oluşturur.

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

'ndaki Kaynak denetimi eklentisi bağlam yapısı.

 lendiği

'ndaki Kaynak denetimi eklentisinin, sağladığı tüm iletişim kutuları için üst öğe olarak kullanabileceği IDE penceresi için bir işleyici.

 lpUser

[in, out] Kullanıcının adı (NULL Sonlandırıcı dahil olmak üzere SCC_USER_SIZE değerini aşmamak için).

 lpProjName

'ndaki Projenin adını tanımlayan dize.

 lpLocalProjPath

'ndaki Projenin çalışma klasörünün yolu.

 lpAuxProjPath

[in, out] Projeyi tanımlayan isteğe bağlı bir yardımcı dize (NULL Sonlandırıcı dahil SCC_AUXPATH_SIZE değerini aşmamak için).

 lpComment açıklaması

'ndaki Oluşturulmakta olan yeni bir projeye yorum yapın.

 lpTextOutProc

'ndaki Kaynak denetim eklentisinden gelen metin çıkışını göstermek için isteğe bağlı bir geri çağırma işlevi.

 dwFlags

'ndaki Proje kaynak denetimi eklentisine bilinmiyorsa yeni bir projenin oluşturulması gerekip gerekmediğini bildirir. Değer `SCC_OP_CREATEIFNEW` ve `SCC_OP_SILENTOPEN.` bir birleşimi olabilir

## <a name="return-value"></a>Dönüş Değeri
 Bu işlevin kaynak denetimi eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Projeyi açmada başarılı oldu.|
|SCC_E_INITIALIZEFAILED|Proje başlatılamadı.|
|SCC_E_INVALIDUSER|Kullanıcı, kaynak denetimi sisteminde oturum açamadı.|
|SCC_E_COULDNOTCREATEPROJECT|Proje çağrıdan önce yoktu;  `SCC_OPT_CREATEIFNEW` bayrağı ayarlandı, ancak proje oluşturulamadı.|
|SCC_E_PROJSYNTAXERR|Geçersiz proje sözdizimi.|
|SCC_E_UNKNOWNPROJECT|Proje, kaynak denetimi eklentisi tarafından bilinmiyor ve `SCC_OPT_CREATEIFNEW` bayrağı ayarlanmadı.|
|SCC_E_INVALIDFILEPATH|Geçersiz veya kullanılamayan dosya yolu.|
|SCC_E_NOTAUTHORIZED|Kullanıcının bu işlemi gerçekleştirmesine izin verilmiyor.|
|SCC_E_ACCESSFAILURE|Büyük olasılıkla ağ veya çekişme sorunlarından dolayı kaynak denetim sistemine erişirken bir sorun oluştu. Yeniden deneme önerilir.|
|SCC_E_NONSPECFICERROR|Özel olmayan bir hata; kaynak denetim sistemi başlatılmadı.|

## <a name="remarks"></a>Açıklamalar
 IDE bir Kullanıcı adı (`lpUser`) ile geçirebilir veya boş bir dizeye bir işaretçi geçirebilir. Bir Kullanıcı adı varsa, kaynak denetimi eklentisi onu varsayılan olarak kullanmalıdır. Ancak, bir ad geçirilmemişse veya oturum açma verilen adla başarısız olursa, eklenti kullanıcıdan oturum açmasını ve geçerli bir oturum açma`.` aldığında geçerli adı `lpUser` döndürür, çünkü eklenti Kullanıcı adı dizesini değiştirebilir IDE, her zaman bir boyut arabelleği ayırır (`SCC_USER_LEN`+ 1 veya SCC_USER_SIZE, null Sonlandırıcı için boşluk içerir).

> [!NOTE]
> IDE 'nin gerçekleştirmesi için gereken ilk eylem `SccOpenProject` işlevine veya [SccGetProjPath](../extensibility/sccgetprojpath-function.md)öğesine çağrı olabilir. Bu nedenle, her ikisi de özdeş `lpUser` parametresine sahiptir.

 `lpAuxProjPath` ve`lpProjName` çözüm dosyasından okur veya `SccGetProjPath` işlevine yapılan çağrıdan döndürülür. Bu parametreler, kaynak denetimi eklentisinin projeyle ilişkilendiğini ve yalnızca eklentiye anlamlı olduğunu içerir. Bu tür dizeler çözüm dosyasında yoksa ve kullanıcıya göz atmayı istenmedi (`SccGetProjPath` işlevi aracılığıyla bir dize döndürüyordu), IDE, her iki `lpAuxProjPath` ve `lpProjName`için boş dizeleri geçirir ve bu değerlerin eklenti tarafından güncelleştirilmesini bekliyor Bu işlev döndürür.

 `lpTextOutProc`, komut sonuç çıkışını görüntüleme amacıyla IDE tarafından kaynak denetimi eklentisine bir geri çağırma işlevinin bir işaretçisidir. Bu geri çağırma işlevi, [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)içinde ayrıntılı olarak açıklanmıştır.

> [!NOTE]
> Kaynak denetimi eklentisi bundan faydalanmasını amaçladığında, [SccInitialize](../extensibility/sccinitialize-function.md)'ın `SCC_CAP_TEXTOUT` bayrağını ayarlamış olması gerekir. Bu bayrak ayarlanmamışsa veya IDE bu özelliği desteklemiyorsa, `lpTextOutProc` `NULL`olur.

 `dwFlags` parametresi, açılan projenin şu anda mevcut olmadığı olaydaki sonucu denetler. İki bitflags, `SCC_OP_CREATEIFNEW` ve `SCC_OP_SILENTOPEN`oluşur. Açılmakta olan proje zaten varsa, işlev yalnızca projeyi açıp `SCC_OK`döndürür. Proje yoksa ve `SCC_OP_CREATEIFNEW` bayrağı açıksa, kaynak denetimi eklentisi projeyi kaynak denetimi sisteminde oluşturabilir, açabilir ve `SCC_OK`döndürebilir. Proje yoksa ve `SCC_OP_CREATEIFNEW` bayrağı kapalıysa, eklenti daha sonra `SCC_OP_SILENTOPEN` bayrağını denetlemelidir. Bu bayrak açık değilse, eklenti kullanıcıdan bir proje adı isteyebilir. Bu bayrak açık ise, eklenti yalnızca `SCC_E_UNKNOWNPROJECT`döndürmelidir.

## <a name="calling-order"></a>Arama sırası
 Normal olay sırasında, bir kaynak denetim oturumu açmak için [SccInitialize](../extensibility/sccinitialize-function.md) ilk olarak çağırılır. Bir oturum, `SccOpenProject`bir çağrıdan ve ardından diğer kaynak denetimi eklentisi API işlev çağrılarına sahip olabilir ve [SccCloseProject](../extensibility/scccloseproject-function.md)çağrısıyla sonlandırılır. Bu tür oturumlar, [Sccunınitialize](../extensibility/sccuninitialize-function.md) çağrılmadan önce birkaç kez yinelenebilir.

 Kaynak denetimi eklentisi `SccInitialize``SCC_CAP_REENTRANT` bitini ayarlarsa, yukarıdaki oturum sırası paralel olarak birçok kez yinelenebilir. Farklı `pvContext` yapıları, her bir `pvContext` tek seferde bir açık projeyle ilişkili farklı oturumları izler. Eklenti,`pvContext` parametresine bağlı olarak, belirli bir çağrıda hangi projeye başvurulduğunu tespit edebilir. Yetenek bit `SCC_CAP_REENTRANT` ayarlanmamışsa, yer içermeyen kaynak denetimi eklentileri birden çok projeyle çalışma olanlarıyla sınırlı olur.

> [!NOTE]
> `SCC_CAP_REENTRANT` bit, kaynak denetimi eklentisi API 'sinin 1,1. sürümünde kullanıma sunulmuştur. Bu, sürüm 1,0 ' de ayarlı değildir veya yok sayılır ve tüm sürüm 1,0 kaynak denetimi eklentileri yeniden kullanılamaz olarak kabul edilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentisi API İşlevleri](../extensibility/source-control-plug-in-api-functions.md)
- [SccCloseProject](../extensibility/scccloseproject-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [SccUninitialize](../extensibility/sccuninitialize-function.md)
- [Dize Uzunluğu Kısıtlamaları](../extensibility/restrictions-on-string-lengths.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)