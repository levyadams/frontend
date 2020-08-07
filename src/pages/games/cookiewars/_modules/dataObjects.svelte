<script context="module">

export const locations = [
    {
        name:'brownstown',
        cookieWeight: .5,
        priceSpread:9,
        riskValue:2,
        safehouse:false,
        safehousePrice:2000,
        safehouseLoot:0,
        localPrices: [
            {name:'semonas',price:0},
            {name:'mintz',price:0},
            {name:'shmores',price:0},
            {name:'chipz',price:0},
            {name:'wagalongs',price:0},
            {name:'patties',price:0}
        ]
    },
     {
        name:'regsville',
        cookieWeight: .55,
        priceSpread:7,
        riskValue:4,
        safehouse:false,
        safehousePrice:2000,
        safehouseLoot:0,
        localPrices: [
            {name:'semonas',price:0},
            {name:'mintz',price:0},
            {name:'shmores',price:0},
            {name:'chipz',price:0},
            {name:'wagalongs',price:0},
            {name:'patties',price:0}
        ]
    },
     {
        name:'midscity',
        cookieWeight: .6,
        priceSpread:4,
        riskValue:6,
        safehouse:false,
        safehousePrice:2000,
        safehouseLoot:0,
        localPrices: [
            {name:'semonas',price:0},
            {name:'mintz',price:0},
            {name:'shmores',price:0},
            {name:'chipz',price:0},
            {name:'wagalongs',price:0},
            {name:'patties',price:0}
        ]
    },
    {
        name:'Le Pew',
        cookieWeight: .75,
        priceSpread:9,
        riskValue:8,
        safehouse:false,
        safehousePrice:2000,
        safehouseLoot:0,
        localPrices: [
            {name:'semonas',price:0},
            {name:'mintz',price:0},
            {name:'shmores',price:0},
            {name:'chipz',price:0},
            {name:'wagalongs',price:0},
            {name:'patties',price:0}
        ]
    }
];

export const cookies = [
    {
        name:'semonas',
        minPrice:2,
        maxPrice:8,
        boxesOwned:0,
    },
    {
        name:'mintz',
        minPrice:2,
        maxPrice:5,
        boxesOwned:0

    },
    {
        name:'shmores',
        minPrice:2,
        maxPrice:5,
        boxesOwned:0
    },
    {
        name:'chipz',
        minPrice:2,
        maxPrice:5,
        boxesOwned:0
    },
    {
        name:'wagalongs',
        minPrice:2,
        maxPrice:5,
        boxesOwned:0
    },
    {
        name:'patties',
        minPrice:2,
        maxPrice:5,
        boxesOwned:0
    }
];

export const inventory = {
    guns:{
        pistol:false,
        ak:false,
        crate:false
    }
};



</script>