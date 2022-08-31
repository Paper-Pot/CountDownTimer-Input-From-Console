<script>
    export let countDownTime
    var deadline = new Date(countDownTime).getTime();
    var now = new Date().getTime();
    var timer;
    var t;
    var time = setInterval(function() {
        var now = new Date().getTime();
        t = deadline - now;
        var days = Math.floor(t / (1000 * 60 * 60 * 24));
        var hours = Math.floor((t%(1000 * 60 * 60 * 24))/(1000 * 60 * 60));
        var minutes = Math.floor((t % (1000 * 60 * 60)) / (1000 * 60));
        var seconds = Math.floor((t % (1000 * 60)) / 1000);
        timer = `${days} : ${hours} : ${minutes} : ${seconds}`
    }, 1000);

</script>

<section>
    <div class="clock">
        <p id="firstP">Limited Time Offer</p>
        <p>Ends in: <span class="demo" style="font-weight:500;">{timer}</span></p>
        <div class="offerContainer">
            <div class="offer">
                <p><b>Get 10% OFF</b></p>
                <p>Use Code:<b> EXAMSTART</b></p>
            </div>
        </div>
    </div>
</section>

<style>

    
</style>