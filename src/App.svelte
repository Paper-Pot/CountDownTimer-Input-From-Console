<script>
  import Timer from "./lib/Timer.svelte"
  let countDownTime="";
  let valEntered = false;
  // console.log("Type duration and input date as console.log(MM/DD/YY)");
    Object.defineProperty(window, "duration", {
      get: function() {
        var oldLog = console.log;
        console.log = function() {
          countDownTime = `${arguments[0]}`;
          if(isValidDate(countDownTime)) valEntered = true
          oldLog.apply(console, arguments);
        }
      }
    });
  function isValidDate(dateString){
    // First check for the pattern
    if(!/^\d{1,2}\/\d{1,2}\/\d{4}$/.test(dateString))
        return false;

    // Parse the date parts to integers
    var parts = dateString.split("/");
    var day = parseInt(parts[1], 10);
    var month = parseInt(parts[0], 10);
    var year = parseInt(parts[2], 10);

    // Check the ranges of month and year
    if(year < 1000 || year > 3000 || month == 0 || month > 12)
        return false;

    var monthLength = [ 31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31 ];

    // Adjust for leap years
    if(year % 400 == 0 || (year % 100 != 0 && year % 4 == 0))
        monthLength[1] = 29;

    // Check the range of the day
    return day > 0 && day <= monthLength[month - 1];
  }
</script>

<main>
  <p> In the console type duration and input date as console.log(MM/DD/YY)
    <br>
    duration -> (Enter)
    <br>
    console.log(MM/DD/YY) -> (enter)

  </p>
  {#if (valEntered)}
    <Timer {countDownTime}/>
  {/if}
</main>

<style>
  p{
    text-align: center;
  }

</style>