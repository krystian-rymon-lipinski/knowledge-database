Jeśli aktywność jest w backstacku, to nie zostaje niszczona!
Np. jeśli A -> B, to na aktywności A nie zostanie wywołane onDestroy(). Natomiast jeśli w B kliknie się wstecz i zostanie zawołane onBackPressed(), to na aktywności B zostanie wywołane onDestroy() - bo nie ma jej już w stacku.

onDestroy() będzie wołane również, jeśli ktoś explicite zawoła finish()