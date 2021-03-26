---
description: Bu işlev, var olan bir kaynak denetimi projesini açar veya yeni bir tane oluşturur.
title: SccOpenProject Işlevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: baada63e84e95fd466e0e5640c592dfe303d8e1a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105063766"
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

[in, out] Kullanıcının adı (NULL Sonlandırıcı dahil SCC_USER_SIZE aşmamak için).

 lpProjName

'ndaki Projenin adını tanımlayan dize.

 lpLocalProjPath

'ndaki Projenin çalışma klasörünün yolu.

 lpAuxProjPath

[in, out] Projeyi tanımlayan isteğe bağlı bir yardımcı dize (NULL Sonlandırıcı dahil SCC_AUXPATH_SIZE aşmamak için).

 lpComment açıklaması

'ndaki Oluşturulmakta olan yeni bir projeye yorum yapın.

 lpTextOutProc

'ndaki Kaynak denetim eklentisinden gelen metin çıkışını göstermek için isteğe bağlı bir geri çağırma işlevi.

 dwFlags

'ndaki Proje kaynak denetimi eklentisine bilinmiyorsa yeni bir projenin oluşturulması gerekip gerekmediğini bildirir. Değer, ve birleşimi olabilir `SCC_OP_CREATEIFNEW``SCC_OP_SILENTOPEN.`

## <a name="return-value"></a>Dönüş Değeri
 Bu işlevin kaynak denetimi eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Projeyi açmada başarılı oldu.|
|SCC_E_INITIALIZEFAILED|Proje başlatılamadı.|
|SCC_E_INVALIDUSER|Kullanıcı, kaynak denetimi sisteminde oturum açamadı.|
|SCC_E_COULDNOTCREATEPROJECT|Proje çağrıdan önce yoktu;  `SCC_OPT_CREATEIFNEW` bayrak ayarlandı, ancak proje oluşturulamadı.|
|SCC_E_PROJSYNTAXERR|Geçersiz proje sözdizimi.|
|SCC_E_UNKNOWNPROJECT|Proje, kaynak denetimi eklentisi için bilinmiyor ve `SCC_OPT_CREATEIFNEW` bayrak ayarlanmadı.|
|SCC_E_INVALIDFILEPATH|Geçersiz veya kullanılamayan dosya yolu.|
|SCC_E_NOTAUTHORIZED|Kullanıcının bu işlemi gerçekleştirmesine izin verilmiyor.|
|SCC_E_ACCESSFAILURE|Büyük olasılıkla ağ veya çekişme sorunlarından dolayı kaynak denetim sistemine erişirken bir sorun oluştu. Yeniden deneme önerilir.|
|SCC_E_NONSPECFICERROR|Özel olmayan bir hata; kaynak denetim sistemi başlatılmadı.|

## <a name="remarks"></a>Açıklamalar
 IDE bir Kullanıcı adı () ile geçirebilir `lpUser` veya bir işaretçiyi boş bir dizeye geçirebiliriz. Bir Kullanıcı adı varsa, kaynak denetimi eklentisi onu varsayılan olarak kullanmalıdır. Ancak, bir ad geçirilmemişse veya oturum açma verilen adla başarısız olursa, eklenti Kullanıcı adı dizesini değiştirebileceğinden, bu, kullanıcının oturum açmasını ve `lpUser` geçerli bir oturum açma zamanı aldığında geçerli adı döndürmesini ister. Bu, IDE, `.` `SCC_USER_LEN` null Sonlandırıcı için boşluk içeren bir boyut arabelleği (+ 1 veya SCC_USER_SIZE) ayırır.

> [!NOTE]
> IDE 'nin gerçekleştirmesi için gereken ilk eylem, `SccOpenProject` işleve veya [SccGetProjPath](../extensibility/sccgetprojpath-function.md)öğesine çağrı olabilir. Bu nedenle, her ikisi de özdeş bir parametreye sahiptir `lpUser` .

 `lpAuxProjPath` ve `lpProjName` çözüm dosyasından okur veya işleve yapılan çağrıdan döndürülür `SccGetProjPath` . Bu parametreler, kaynak denetimi eklentisinin projeyle ilişkilendiğini ve yalnızca eklentiye anlamlı olduğunu içerir. Bu tür dizeler çözüm dosyasında yoksa ve kullanıcıya göz atmayı (işlev aracılığıyla bir dize döndüren `SccGetProjPath` ) beklemiyorsa, IDE boş dizeleri hem hem de için geçirir `lpAuxProjPath` `lpProjName` ve bu değer, bu işlevin döndürdüğü eklenti tarafından güncelleştirilmesini bekler.

 `lpTextOutProc` , komut sonuç çıkışını görüntüleme amacıyla IDE tarafından kaynak denetimi eklentisine bir geri çağırma işlevi için bir işaretçisidir. Bu geri çağırma işlevi, [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)içinde ayrıntılı olarak açıklanmıştır.

> [!NOTE]
> Kaynak denetimi eklentisi bundan faydalanmasını amaçladığında, `SCC_CAP_TEXTOUT` [SccInitialize](../extensibility/sccinitialize-function.md)'ın bayrağını ayarlamış olması gerekir. Bu bayrak ayarlanmamışsa veya IDE bu özelliği desteklemiyorsa, olur `lpTextOutProc` `NULL` .

 `dwFlags`Parametresi, açılan projenin şu anda mevcut olmadığı olaydaki sonucu denetler. İki bitflags `SCC_OP_CREATEIFNEW` ve ile oluşur `SCC_OP_SILENTOPEN` . Açılmakta olan proje zaten varsa, işlev projeyi açar ve döndürür `SCC_OK` . Proje yoksa ve `SCC_OP_CREATEIFNEW` bayrak açıksa, kaynak denetimi eklentisi projeyi kaynak denetimi sisteminde oluşturabilir, açabilir ve döndürebilir `SCC_OK` . Proje yoksa ve `SCC_OP_CREATEIFNEW` bayrak kapalıysa, eklenti daha sonra bayrağı denetlemelidir `SCC_OP_SILENTOPEN` . Bu bayrak açık değilse, eklenti kullanıcıdan bir proje adı isteyebilir. Bu bayrak açık ise, eklenti basitçe döndürülür `SCC_E_UNKNOWNPROJECT` .

## <a name="calling-order"></a>Arama sırası
 Normal olay sırasında, bir kaynak denetim oturumu açmak için [SccInitialize](../extensibility/sccinitialize-function.md) ilk olarak çağırılır. Bir oturum, bir çağrısından `SccOpenProject` , ardından diğer kaynak denetimi EKLENTISI API işlev çağrılarına sahip olabilir ve [SccCloseProject](../extensibility/scccloseproject-function.md)çağrısıyla sonlandırılır. Bu tür oturumlar, [Sccunınitialize](../extensibility/sccuninitialize-function.md) çağrılmadan önce birkaç kez yinelenebilir.

 Kaynak denetimi eklentisi `SCC_CAP_REENTRANT` içinde bit ayarlarsa `SccInitialize` , yukarıdaki oturum sırası paralel olarak birçok kez yinelenebilir. Farklı `pvContext` yapılar, her birinin `pvContext` tek seferde bir açık projeyle ilişkilendirildiği farklı oturumları izler. `pvContext`Parametresi temelinde, eklenti hangi projeye belirli bir çağrıda başvurulduğunu belirleyebilir. Yetenek biti `SCC_CAP_REENTRANT` ayarlanmamışsa, yer içermeyen kaynak denetimi eklentileri birden çok projeyle çalışma olanlarıyla sınırlı olur.

> [!NOTE]
> `SCC_CAP_REENTRANT`Bit, kaynak denetimi EKLENTISI API 'sinin sürüm 1,1 ' de tanıtılmıştı. Bu, sürüm 1,0 ' de ayarlı değildir veya yok sayılır ve tüm sürüm 1,0 kaynak denetimi eklentileri yeniden kullanılamaz olarak kabul edilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentisi API İşlevleri](../extensibility/source-control-plug-in-api-functions.md)
- [SccCloseProject](../extensibility/scccloseproject-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [SccUninitialize](../extensibility/sccuninitialize-function.md)
- [Dize Uzunluğu Kısıtlamaları](../extensibility/restrictions-on-string-lengths.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
