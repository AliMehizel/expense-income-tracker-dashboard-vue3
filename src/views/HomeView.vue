<template>
  <main>
    <!--side_bar_section-->
    <div class="side-bar">
      <!--user_card-->
      <div class="user-card">
        <img src="../assets/images/user-icon.png" id="user-avatar" alt="user-icon-avatar">
        
        <div class="burger-menu" @click="handleBurger" >
          <i class="material-icons" >menu</i>
        </div>
        <div class="user-menu" :id="show ? 'animate': ''">
          <ul class="user-links">
          <h3>Menu</h3>
          <li><i class="material-icons">person</i> John doe</li>
          <li><i class="material-icons">home</i> Home</li>
          <li><i class="material-icons">tune</i> Settings</li>
        </ul>
        <!--options links-->
        
        <ul class="options-links">
          <h3>Options</h3>
          <li><i class="material-icons">notifications</i> Notify</li>
          <li><i class="material-icons">credit_card</i> Cards</li>
          <li><i class="material-icons">schedule</i> Recents</li>
          <li><i class="material-icons">payments</i> Payments</li>
          <br>
          <br>
          <br>
          <br>
          <li><i class="material-icons">logout</i> Logout</li>
        </ul>
        </div>
      </div>
    </div>
    <!--main_section-->
    <div class="main-container">
      <!--utils container-->
      <div class="utils-container">
        <p>August,03</p>
        <i class="material-icons" id="dark_mode_icons" @click="handleClick">dark_mode</i>
      </div>
      <!--box_section-->
      <div class="box-section">
        <div class="income-box">
          <div class="span-title">
            <p>Income</p>
            <i class="material-icons">arrow_upward</i>
          </div>
          <div>
            <strong>185k</strong>
          </div>
        </div>
        <div class="expense-box">
          <div class="span-title">
            <p>Expense</p>
            <i class="material-icons">arrow_downward</i>
          </div>
          <div>
            <strong>120k</strong>
          </div>
        </div>
        <div class="currency-box">
          <img src="../assets/images/currency_dollar.png" alt="dollar_currency">
        </div>
      </div>
      <!--chart container-->
      <div class="chart-container">
        <Line :data="chart" :options="options" class="line-chart"/>
      </div>
      <!--button-container-->
      <div class="btn-container">
        <h4>Latest transactions</h4>
        <button class="add-btn" ><i class="material-icons">add</i> Add transactions</button>
      </div>
      <!--inc/exp list-->
      <div class="transaction-list">
        <div class="list-child">
          <div>
            Description
          </div>
          <div>
            Amount
          </div>
          <div>
            Date
          </div>
          <div>
            <i class="material-icons" id="exp-icon" >arrow_downward</i>
          </div>
        </div>

        <div class="list-child">
          <div>
            Buy a car
          </div>
          <div>
            120$
          </div>
          <div>
            27/07/2019
          </div>
          <div>
            <i class="material-icons" id="exp-icon" >arrow_downward</i>
          </div>
        </div>

        <div class="list-child">
          <div>
            Buy a car
          </div>
          <div>
            120$
          </div>
          <div>
            27/07/2019
          </div>
          <div>
            <i class="material-icons" id="inc-icon" >arrow_upward</i>
          </div>
      </div>

      <div class="list-child">
          <div>
            Buy a car
          </div>
          <div>
            120$
          </div>
          <div>
            27/07/2019
          </div>
          <div>
            <i class="material-icons" id="exp-icon" >arrow_downward</i>
          </div>
        </div>

        <div class="list-child">
          <div>
            Buy a car
          </div>
          <div>
            120$
          </div>
          <div>
            27/07/2019
          </div>
          <div>
            <i class="material-icons" id="inc-icon" >arrow_upward</i>
          </div>
      </div>

      </div>
    </div>
  </main>
</template>

<script setup>
import { Line} from 'vue-chartjs'
import {
  Chart as ChartJS,
  CategoryScale,
  LinearScale,
  PointElement,
  LineElement,
  Title,
  Tooltip,
  Legend
} from 'chart.js'
import { ref } from 'vue';

ChartJS.register(
  CategoryScale,
  LinearScale,
  PointElement,
  LineElement,
  Title,
  Tooltip,
  Legend
)




//chartjs
const chart = {
  labels:['January', 'February', 'March', 'April', 'May', 'June', 'July'],
  datasets: [{
    label: 'Expense',
    data: [65, 59, 80, 81, 56, 55, 40],
    fill: false,
    borderColor: '#ef233c',
    tension: 0.1
  },
  {
    label: 'Income',
    data: [45, 52, 70, 91, 56, 45, 70],
    fill: false,
    borderColor: '#183D3D',
    tension: 0.1
  }],

};

const options = {
  responsive: true,
  maintainAspectRatio: false
}
//handle transactions & form input component

//light/dark mode

const app = document.body
function handleClick(){
  app.classList.toggle('app')
}

//burger menu
let show = ref(false)
function handleBurger (){
  show.value = !show.value
}


</script>

<style scoped>
/*|| main container */
main{
  width: 100%;
  display: grid;
  grid-template-columns: repeat(12,1fr);
}
/*|| side bar */
.side-bar{
  grid-column: 1 / span 3;
  display: flex;
  align-items: start;
  justify-content: end;
  height: 100vh;
}
.user-card{
  margin-top: 50px;
  display: flex;
  justify-content: start;
  align-items: center;
  flex-direction: column;
  background-color: #183D3D;
  border: 2px solid #5C8374;
  width: 80%;
  padding: 15px;
  height: 90vh;
  border-radius: 6px;
  box-shadow: 0px 10px 15px -3px rgba(0,0,0,0.1);
}
.user-card h3{
  margin: 10px 0;
  font-weight: 550;
  font-size: 20px;
  color: #fff;
}
ul{
  display: flex;
  align-items: flex-start;
  flex-direction: column;
  justify-content: center;
}
li{
  margin: 5px 0;
  list-style: none;
  display: flex;
  align-items: center;
  cursor: pointer;
  font-size: 14px;
  color: #c3c3c3;
}

li:hover{
  transition: 0.2s all ease-in-out;
  color: #fff;
}
li i{
  margin-right: 12px;
}
#user-avatar{
  margin-top: 50px;
  width: 90px;
  height: 90px;
  border-radius: 50%;
  border: 3px solid #5C8374;
  cursor: pointer;
}
/*||burger meenu */
.burger-menu{
  display: none;
}
.burger-menu i{
  margin-top: 15px;
  font-size: 40px;
  color: #c3c3c3;
  cursor: pointer;
}
/*|| main section*/
.main-container{
  grid-column: 4 / span 12;
  display: flex;
  justify-content: flex-start;
  align-items: center;
  flex-direction: column;
}
/*||utils container */

.utils-container{
  margin-top: 70px;
  padding: 0 5px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 75%;
}



#dark_mode_icons{
  cursor: pointer;
  font-size: 30px;
}
/*||box section */
.box-section{
  padding: 30px 0;
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 75%;
}

.box-section > div{
  width: 150px;
  height: 90px;
  border-radius: 6px;
  border: none;
  text-align: center;
  display: flex;
  align-items: start;
  justify-content: center;
 /*  box-shadow: 0px 0px 4px 8px rgba(0,0,0,0.1); */
 box-shadow: 0px 10px 15px -3px rgba(0,0,0,0.1);
  padding: 7px;
}



.expense-box{
  color: black;
  background: #fff;
  display: flex;
  align-items: center;
  flex-direction: column;
}


.expense-box i{
  color: #ef233c;
  border: 2px solid #ef233c;
}
.income-box{
  background: #fff;
  color: #000;
  display: flex;
  align-items: center;
  flex-direction: column;
}
.income-box i{
  color: #183D3D;
  border: 2px solid #183D3D;
}

.box-section i{
  font-size: 25px;
  border-radius: 50%;
  font-weight: 800;
}
.box-section strong{
  font-size: 28px;
}

.box-section p {
  font-size: 14px;
  font-weight: 600;
}
.span-title{
  display: flex;
  align-items: start;
  justify-content: space-between;
  width: 100%;
}
.currency-box{
  background-color: #183D3D;
  
}
.currency-box img{
  width: 130px;
  height: 90px;
  object-fit: contain;
}

/*||chart container */
.chart-container{
  display: flex;
  align-items: center;
  justify-content: center;
  border: 1px solid #444;
  height: 350px;
  width: 75%;
  padding: 10px;
  border-radius: 6px;
}


/*|| btn container*/
.btn-container{
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 75%;
  gap: 30px;
  padding: 15px 5px;
}

.btn-container h4{
  font-weight: 500;
}

.btn-container button{
  padding: 5px 20px;
  font-size: 16px;
  border-radius: 6px;
  font-family: 'Poppins', sans-serif;
  border: 2px solid #93B1A6;
  color: #93B1A6;
  background-color: transparent;
  display: flex;
  align-items: center;
  cursor: pointer;
}

.add-btn:hover{
  background: #5C8374;
  color: #fff;
}

/*|| transaction list*/
.transaction-list{
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  width: 100%;
  
}

.transaction-list > div{
  margin-top: 5px;
  width: 75%;
  display: flex;
  align-items: center;
  justify-content: space-evenly;
  border:none;
  padding: 10px 0;
  background: #5C8374;
  border-radius: 4px;
  box-shadow: 0px 10px 15px -3px rgba(0,0,0,0.1);
  
}

.list-child > div {
  flex: 1;
  text-align: center;
  color: #000;
}

#exp-icon{
  color: #ef233c;
  vertical-align: middle;
  border: 2px solid #ef233c;
  border-radius: 50%;
}

#inc-icon{
  color: #183D3D;
  vertical-align: middle;
  border: 2px solid #183D3D;
  border-radius: 50%;
}

@media screen and (max-width:768px) {
  main{
    grid-template-columns: 1fr;
    grid-template-rows: repeat(1fr,12);
    place-items: center;
  }
  /*||side bar */
  .side-bar{
    grid-row: span 1;
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100%;
    height: 100%;

    
  }
  
  .user-card{
    padding: 40px 10px;
    margin: 20px 0 0 0;
    width: 78%;
    height: 70px;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
    position: relative;
  }
  .user-card .user-menu {
    display: flex;
    justify-content:flex-start;
    align-items: center;
    flex-direction: column;
    padding: 10px 0;
    position: absolute;
    top: 82px;
    right: 0;
    width: 100%;
    height: 90vh;
    background: #183D3D;
    opacity: 0;
    transition: all 0.5s  ease-in-out;
  }

  #animate{
    
    transition: all 0.5s  ease-in-out;
    z-index: 1;
    display: flex;
    justify-content: flex-start;
    align-items: center;
    flex-direction: column;
    opacity: 1;
  }

  .user-links{
    margin-top: 50px;
  }

  #user-avatar{
    margin: 0;
    width: 65px;
    height: 65px;
  }
  
  
/*||main container */
  .main-container{
    grid-column: span 1;
    grid-row: 2 / span 12;
    min-width: 100%;
  }

  /*||box-section */
  .box-section > div {
    width: 100px;
    height: 70px;
  }

  .box-section > div strong{
    font-size: 20px;
  }

  .span-title p{
    font-size: 12px;
  }

  .currency-box img{
    width: 100px;
    height: 70px;
  }
  /*||burger menu */
  .burger-menu{
  display: block;
}

}

@media screen and (max-width:425px) {
  /*|| box section */
  .box-section{
    width: 95%;
  }
}
</style>