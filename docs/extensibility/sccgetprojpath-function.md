---
title: SccGetProjPath Fonksiyonu | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetProjPath
helpviewer_keywords:
- SccGetProjPath function
ms.assetid: 1079847e-d45f-4cb8-9d92-1e01ce5d08f6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 281787da3499c081fbbe6f59b7b8175a4dbf24d7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700700"
---
# <a name="sccgetprojpath-function"></a>SccGetProjPath fonksiyonu
Bu işlev, kullanıcıyı yalnızca kaynak denetim eklentisi için anlamlı olan bir dize olan bir proje yolu için ister. Kullanıcı şu zaman çağrılır:

- Yeni bir proje oluşturma

- Sürüm denetimine varolan bir proje ekleme

- Varolan bir sürüm denetim projesini bulmaya çalışma

## <a name="syntax"></a>Sözdizimi

```cpp
SCCRTN SccGetProjPath (
   LPVOID pvContext,
   HWND   hWnd,
   LPSTR  lpUser,
   LPSTR  lpProjName,
   LPSTR  lpLocalPath,
   LPSTR  lpAuxProjPath,
   BOOL   bAllowChangePath,
   LPBOOL pbNew
);
```

### <a name="parameters"></a>Parametreler
 pvContext

[içinde] Kaynak denetimi eklentisi bağlam yapısı.

 Hwnd

[içinde] Kaynak denetim eklentisinin sağladığı tüm iletişim kutuları için üst öğe olarak kullanabileceği IDE penceresine bir tanıtıcı.

 lpUser

[içinde, dışarı] Kullanıcı adı (NULL sonlandırıcı dahil olmak üzere SCC_USER_SIZE geçmemelidir)

 lpProjName

[içinde, dışarı] IDE projesinin adı, proje çalışma alanı veya makefile (NULL sonlandırıcıdahil SCC_PRJPATH_SIZE'i geçmemek üzere).

 lpLocalPath

[içinde, dışarı] Projenin çalışma yolu. `bAllowChangePath` Ise, `TRUE`kaynak denetim eklentisi bu dizeyi değiştirebilir (null-terminator dahil _MAX_PATH aşmayacak).

 lpAuxProjPath

[içinde, dışarı] Döndürülen proje yolu için bir arabellek (NULL sonlandırıcı dahil SCC_PRJPATH_SIZE'i geçmez).

 bAllowChangePath

[içinde] Bu durumda, `TRUE`kaynak denetim eklentisi için istekte bulunabilir ve dizeyi `lpLocalPath` değiştirebilir.

 pbYeni

[içinde, dışarı] Gelen değer, yeni bir proje oluşturup oluşturmayacağını gösterir. Döndürülen değer, proje oluşturmanın başarısını gösterir:

|Gelen|Yorum|
|--------------|--------------------|
|TRUE|Kullanıcı yeni bir proje oluşturabilir.|
|FALSE|Kullanıcı yeni bir proje oluşturamayabilir.|

|Giden|Yorum|
|--------------|--------------------|
|TRUE|Yeni bir proje oluşturuldu.|
|FALSE|Varolan bir proje seçildi.|

## <a name="return-value"></a>Döndürülen değer
 Bu işlevin kaynak denetim eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Proje başarıyla oluşturuldu veya geri alındı.|
|SCC_I_OPERATIONCANCELED|İşlem iptal edildi.|
|SCC_E_ACCESSFAILURE|Kaynak denetim sistemine erişmede büyük olasılıkla ağ veya çekişme sorunları nedeniyle bir sorun vardı.|
|SCC_E_CONNECTIONFAILURE|Kaynak kontrol sistemine bağlanmaya çalışırken bir sorun vardı.|
|SCC_E_NONSPECIFICERROR|Belirtilmeyen bir hata oluştu.|

## <a name="remarks"></a>Açıklamalar
 Bu fonksiyonun amacı IDE parametreleri `lpProjName` elde `lpAuxProjPath`etmek ve . Kaynak denetimi eklentisi kullanıcıdan bu bilgileri istedikten sonra, bu iki dizeyi IDE'ye geri geçirir. IDE bu dizeleri çözüm dosyasında devam eder ve kullanıcı bu projeyi açtığında [Bunları SccOpenProject'e](../extensibility/sccopenproject-function.md) geçirir. Bu dizeleri eklentibir proje ile ilişkili bilgileri izlemek için etkinleştirin.

 İşlev ilk çağrıldığında, `lpAuxProjPath` boş bir dize olarak ayarlanır. `lProjName`ayrıca boş olabilir veya kaynak denetim eklentisinin kullanabileceği veya yok sayabileceği IDE proje adını içerebilir. İşlev başarıyla döndüğünde, eklenti karşılık gelen iki dizeyi döndürür. IDE bu dizeleri hakkında hiçbir varsayımda bulunmaz, bunları kullanmaz ve kullanıcının bunları değiştirmesine izin vermez. Kullanıcı ayarları değiştirmek isterse, IDE önceki `SccGetProjPath` kez aldığı değerlerle aynı değerleri geçirerek yeniden arar. Bu, eklentiye bu iki dize üzerinde tam denetim sağlar.

 Için, `lpUser`IDE bir kullanıcı adı geçebilir veya sadece boş bir dize için bir işaretçi geçebilir. Bir kullanıcı adı varsa, kaynak denetim eklentisi varsayılan olarak kullanmalıdır. Ancak, hiçbir ad geçirilirse veya giriş verilen adla başarısız olduysa, eklenti kullanıcıdan oturum açma için `lpUser` istekte bulunmalı ve geçerli bir giriş aldığında adı geri geçirmelidir. Eklenti bu dizeyi değiştirebileceğinden, IDE her zaman bir boyut`SCC_USER_LEN`arabelleği (+1) ayırır.

> [!NOTE]
> IDE'nin gerçekleştirdiği ilk `SccOpenProject` eylem, işlev veya `SccGetProjPath` işlev için bir çağrı olabilir. Bu nedenle, her ikisi `lpUser` de kaynak denetim eklentisi her iki anda kullanıcı oturum açmak için sağlayan aynı parametre vardır. İşlevden dönüş bir hata belirtse bile, eklentinin bu dizeyi geçerli bir giriş adı ile doldurması gerekir.

 `lpLocalPath`kullanıcının projeyi sakladığı dizindir. Boş bir ip olabilir. Şu anda tanımlanmış bir dizin yoksa (kaynak denetim sisteminden proje indirmeye çalışan bir `bAllowChangePath` `TRUE`kullanıcı nın durumunda olduğu gibi) ve ise, kaynak denetim eklentisi kullanıcıdan giriş için isteyebilir veya kendi dizesini `lpLocalPath`. `bAllowChangePath` Varsa, `FALSE`kullanıcı zaten belirtilen dizinde çalışıyor, çünkü eklenti dize değiştirmemelidir.

 Kullanıcı kaynak denetimi altına alınacak yeni bir proje oluşturursa, kaynak denetim eklentisi aslında kaynak denetim `SccGetProjPath` sisteminde o anda oluşturmak olmayabilir denir. Bunun yerine, için sıfır olmayan bir değer `pbNew`ile birlikte dize geri geçer , projenin kaynak denetim sisteminde oluşturulacağını belirten.

 Örneğin, Visual Studio'daki **Yeni Proje** sihirbazındaki bir kullanıcı projesini kaynak denetimine eklerse, Visual Studio bu işlevi çağırır ve eklenti, Visual Studio projesini içerecek kaynak denetim sisteminde yeni bir proje oluşturmanın uygun olup olmadığını belirler. Kullanıcı sihirbazı tamamlamadan önce **İptal'i** tıklatıyorsa, proje hiçbir zaman oluşturulmaz. Kullanıcı **Tamam'ı**tıklatıyorsa, Visual Studio çağırır, `SccOpenProject`içeri geçer `SCC_OPT_CREATEIFNEW`ve kaynak kontrollü proje o anda oluşturulur.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak kontrol eklentisi API fonksiyonları](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
