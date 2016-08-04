Usually, errors that occur inside a coroutine do not get reported, which can lead to all sorts of coding catastrophes. To fix, include the following code before any use of coroutine.resume

Code
----

    _coroutine_resume = coroutine.resume
    function coroutine.resume(...)
        local state,result = _coroutine_resume(...)
        if not state then
            outputDebugString( tostring(result), 1 )    -- Output error message
        end
        return state,result
    end

See Also
--------
