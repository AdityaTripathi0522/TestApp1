library(shiny)
library(shinythemes)
library(ggplot2)
library(shinyWidgets) # For enhanced UI elements

# Define Western zodiac date ranges and constellations data
western_zodiac_data <- list(
  "Aries" = list(
    date_range = c("March 21", "April 19"),
    stars = data.frame(
      x = c(1, 2, 3, 4, 3.5, 2.5),
      y = c(1, 2, 1.5, 1, 3, 3.5),
      name = c("Hamal", "Sheratan", "Mesarthim", "Botein", "41 Ari", "35 Ari")
    ),
    lines = data.frame(
      x = c(1, 2, 2, 3, 3, 4, 2, 2.5, 2.5, 3.5),
      y = c(1, 2, 2, 1.5, 1.5, 1, 2, 3.5, 3.5, 3),
      group = c(1, 1, 2, 2, 3, 3, 4, 4, 5, 5)
    ),
    info = "Aries represents the Ram in Greek mythology, specifically the golden ram that rescued Phrixus and took him to Colchis. The brightest star in Aries is Hamal, which means 'head of the ram'."
  ),
  "Taurus" = list(
    date_range = c("April 20", "May 20"),
    stars = data.frame(
      x = c(1, 2, 3, 4, 3, 2.5, 4.5),
      y = c(1, 2, 1.5, 2.5, 3, 4, 3.5),
      name = c("Aldebaran", "Elnath", "Alcyone", "Maia", "Pleione", "Atlas", "Merope")
    ),
    lines = data.frame(
      x = c(1, 2, 2, 3, 3, 4, 3, 2.5, 2.5, 3, 4, 4.5),
      y = c(1, 2, 2, 1.5, 1.5, 2.5, 3, 4, 4, 3, 2.5, 3.5),
      group = c(1, 1, 2, 2, 3, 3, 4, 4, 5, 5, 6, 6)
    ),
    info = "Taurus represents the Bull in Greek mythology. The constellation features the bright star Aldebaran and contains the famous star cluster Pleiades. Taurus is one of the oldest constellations, dating back to the Early Bronze Age."
  ),
  "Gemini" = list(
    date_range = c("May 21", "June 20"),
    stars = data.frame(
      x = c(1, 2, 3, 2.5, 3.5, 4, 5),
      y = c(1, 2, 3, 1.5, 2.5, 1, 2),
      name = c("Pollux", "Castor", "Alhena", "Wasat", "Mebsuta", "Propus", "Tejat")
    ),
    lines = data.frame(
      x = c(1, 2, 2, 3, 2, 2.5, 2.5, 3.5, 3.5, 4, 4, 5),
      y = c(1, 2, 2, 3, 2, 1.5, 1.5, 2.5, 2.5, 1, 1, 2),
      group = c(1, 1, 2, 2, 3, 3, 4, 4, 5, 5, 6, 6)
    ),
    info = "Gemini represents the twins Castor and Pollux in Greek mythology. The two brightest stars in Gemini are named after these twins. Pollux is an orange giant star and Castor is actually a system of six stars."
  ),
  "Cancer" = list(
    date_range = c("June 21", "July 22"),
    stars = data.frame(
      x = c(2, 3, 4, 3, 2.5),
      y = c(2, 3, 2, 1, 3.5),
      name = c("Acubens", "Asellus Borealis", "Asellus Australis", "Altarf", "Tegmine")
    ),
    lines = data.frame(
      x = c(2, 3, 3, 4, 4, 3, 3, 2.5),
      y = c(2, 3, 3, 2, 2, 1, 3, 3.5),
      group = c(1, 1, 2, 2, 3, 3, 4, 4)
    ),
    info = "Cancer represents the Crab in Greek mythology that Hera sent to distract Hercules during his fight with the Hydra. The constellation contains a star cluster called the Beehive Cluster (M44), which is visible to the naked eye."
  ),
  "Leo" = list(
    date_range = c("July 23", "August 22"),
    stars = data.frame(
      x = c(1, 2, 3, 4, 2.5, 3.5, 5),
      y = c(1, 2, 1.5, 2.5, 3, 3.5, 1),
      name = c("Regulus", "Algieba", "Zosma", "Denebola", "Adhafera", "Alterf", "Subra")
    ),
    lines = data.frame(
      x = c(1, 2, 2, 3, 3, 4, 4, 2.5, 2.5, 3.5, 3, 5),
      y = c(1, 2, 2, 1.5, 1.5, 2.5, 2.5, 3, 3, 3.5, 1.5, 1),
      group = c(1, 1, 2, 2, 3, 3, 4, 4, 5, 5, 6, 6)
    ),
    info = "Leo represents the Nemean Lion in Greek mythology, which was killed by Hercules as one of his twelve labors. The constellation is dominated by the bright star Regulus, often called the 'Heart of the Lion'."
  ),
  "Virgo" = list(
    date_range = c("August 23", "September 22"),
    stars = data.frame(
      x = c(1, 2, 3, 4, 3.5, 2.5, 1.5),
      y = c(1, 2, 3, 2, 1, 3.5, 2.5),
      name = c("Spica", "Vindemiatrix", "Porrima", "Auva", "Zavijava", "Zaniah", "Heze")
    ),
    lines = data.frame(
      x = c(1, 2, 2, 3, 3, 4, 4, 3.5, 3.5, 2.5, 2.5, 1.5),
      y = c(1, 2, 2, 3, 3, 2, 2, 1, 1, 3.5, 3.5, 2.5),
      group = c(1, 1, 2, 2, 3, 3, 4, 4, 5, 5, 6, 6)
    ),
    info = "Virgo is one of the largest constellations and represents a maiden holding an ear of wheat (the star Spica). In various mythologies, she is associated with harvest goddesses. Spica is one of the brightest stars in the night sky."
  ),
  "Libra" = list(
    date_range = c("September 23", "October 22"),
    stars = data.frame(
      x = c(1, 2.5, 4, 3, 2),
      y = c(1, 2, 1, 3, 3.5),
      name = c("Zubenelgenubi", "Zubeneschamali", "Zubenelhakrabi", "Brachium", "Iota Librae")
    ),
    lines = data.frame(
      x = c(1, 2.5, 2.5, 4, 2.5, 3, 3, 2),
      y = c(1, 2, 2, 1, 2, 3, 3, 3.5),
      group = c(1, 1, 2, 2, 3, 3, 4, 4)
    ),
    info = "Libra represents the Scales of Justice in mythology, often associated with balance and harmony. It's the only zodiac constellation that represents an inanimate object rather than an animal or person."
  ),
  "Scorpio" = list(
    date_range = c("October 23", "November 21"),
    stars = data.frame(
      x = c(1, 2, 3, 4, 3.5, 2.5, 1.5, 4.5),
      y = c(1, 2, 1.5, 1, 2.5, 3, 3.5, 0.5),
      name = c("Antares", "Acrab", "Dschubba", "Sargas", "Lesath", "Shaula", "Jabbah", "Girtab")
    ),
    lines = data.frame(
      x = c(1, 2, 2, 3, 3, 4, 4, 4.5, 3, 3.5, 3.5, 2.5, 2.5, 1.5),
      y = c(1, 2, 2, 1.5, 1.5, 1, 1, 0.5, 1.5, 2.5, 2.5, 3, 3, 3.5),
      group = c(1, 1, 2, 2, 3, 3, 4, 4, 5, 5, 6, 6, 7, 7)
    ),
    info = "Scorpio represents the Scorpion in Greek mythology that killed Orion the Hunter. The constellation features the bright red star Antares, whose name means 'rival of Mars' due to its reddish appearance similar to the planet."
  ),
  "Sagittarius" = list(
    date_range = c("November 22", "December 21"),
    stars = data.frame(
      x = c(1, 2, 3, 4, 2.5, 3.5, 1.5),
      y = c(1, 2, 3, 2, 1.5, 2.5, 0.5),
      name = c("Kaus Australis", "Nunki", "Kaus Media", "Kaus Borealis", "Ascella", "Albaldah", "Rukbat")
    ),
    lines = data.frame(
      x = c(1, 2, 2, 3, 3, 4, 4, 2.5, 2.5, 3.5, 1, 1.5),
      y = c(1, 2, 2, 3, 3, 2, 2, 1.5, 1.5, 2.5, 1, 0.5),
      group = c(1, 1, 2, 2, 3, 3, 4, 4, 5, 5, 6, 6)
    ),
    info = "Sagittarius represents the Archer, often depicted as a centaur with a bow and arrow. The constellation is located in the direction of the center of our Milky Way galaxy, making it rich in star clusters and nebulae."
  ),
  "Capricorn" = list(
    date_range = c("December 22", "January 19"),
    stars = data.frame(
      x = c(1, 2, 3, 2.5, 1.5, 3.5),
      y = c(1, 2, 1, 3, 2.5, 2),
      name = c("Deneb Algedi", "Dabih", "Nashira", "Algedi", "Yen", "Dorsum")
    ),
    lines = data.frame(
      x = c(1, 2, 2, 3, 3, 3.5, 2, 2.5, 2.5, 1.5),
      y = c(1, 2, 2, 1, 1, 2, 2, 3, 3, 2.5),
      group = c(1, 1, 2, 2, 3, 3, 4, 4, 5, 5)
    ),
    info = "Capricorn represents a goat with a fish's tail in mythology. It's one of the faintest zodiac constellations but has cultural significance as it marks the southern-most point reached by the sun during winter solstice."
  ),
  "Aquarius" = list(
    date_range = c("January 20", "February 18"),
    stars = data.frame(
      x = c(1, 2, 3, 4, 2.5, 3.5, 1.5),
      y = c(1, 2, 3, 2, 2.5, 1.5, 2.5),
      name = c("Sadalsuud", "Sadalmelik", "Sadachbia", "Skat", "Eta Aquarii", "Zeta Aquarii", "Sadaltager")
    ),
    lines = data.frame(
      x = c(1, 2, 2, 3, 3, 4, 4, 3.5, 2, 2.5, 2.5, 1.5),
      y = c(1, 2, 2, 3, 3, 2, 2, 1.5, 2, 2.5, 2.5, 2.5),
      group = c(1, 1, 2, 2, 3, 3, 4, 4, 5, 5, 6, 6)
    ),
    info = "Aquarius represents the Water Bearer in mythology. Many of its star names begin with 'Sad', which means 'luck' in Arabic. The constellation contains the interesting planetary nebula called the Saturn Nebula."
  ),
  "Pisces" = list(
    date_range = c("February 19", "March 20"),
    stars = data.frame(
      x = c(1, 3, 5, 2, 4, 3, 2.5),
      y = c(1, 3, 1, 2, 2, 0.5, 1.5),
      name = c("Alrescha", "Alpherg", "Torcularis", "Samakah", "Tish", "Fum al Samakah", "Kullat Nunu")
    ),
    lines = data.frame(
      x = c(1, 2, 2, 2.5, 2.5, 3, 3, 4, 4, 5, 3, 3, 1),
      y = c(1, 2, 2, 1.5, 1.5, 0.5, 0.5, 2, 2, 1, 0.5, 3, 1),
      group = c(1, 1, 2, 2, 3, 3, 4, 4, 5, 5, 6, 6, 7)
    ),
    info = "Pisces represents the Fish in mythology, specifically two fish tied together with a cord. In Greek mythology, Aphrodite and Eros transformed into fish to escape the monster Typhon."
  )
)

# Define Vedic (Jyotish) zodiac data 
# Note: Vedic astrology uses the same constellations but with different date ranges due to sidereal calculations
vedic_zodiac_data <- list(
  "Mesha (Aries)" = list(
    date_range = c("April 14", "May 14"),
    stars = western_zodiac_data[["Aries"]]$stars,
    lines = western_zodiac_data[["Aries"]]$lines,
    info = "In Vedic astrology, Mesha (Ram) is ruled by Mars and represents new beginnings, leadership, and courage. It's associated with the head in the body and with fire element."
  ),
  "Vrishabha (Taurus)" = list(
    date_range = c("May 15", "June 14"),
    stars = western_zodiac_data[["Taurus"]]$stars,
    lines = western_zodiac_data[["Taurus"]]$lines,
    info = "Vrishabha (Bull) is ruled by Venus in Vedic astrology. It represents stability, determination, and material comforts. It's associated with the throat and earth element."
  ),
  "Mithuna (Gemini)" = list(
    date_range = c("June 15", "July 14"),
    stars = western_zodiac_data[["Gemini"]]$stars,
    lines = western_zodiac_data[["Gemini"]]$lines,
    info = "Mithuna (Twins) is ruled by Mercury in Vedic astrology. It represents communication, duality, and adaptability. It's associated with the arms/shoulders and air element."
  ),
  "Karka (Cancer)" = list(
    date_range = c("July 15", "August 14"),
    stars = western_zodiac_data[["Cancer"]]$stars,
    lines = western_zodiac_data[["Cancer"]]$lines,
    info = "Karka (Crab) is ruled by the Moon in Vedic astrology. It represents emotions, nurturing, and home. It's associated with the chest and water element."
  ),
  "Simha (Leo)" = list(
    date_range = c("August 15", "September 15"),
    stars = western_zodiac_data[["Leo"]]$stars,
    lines = western_zodiac_data[["Leo"]]$lines,
    info = "Simha (Lion) is ruled by the Sun in Vedic astrology. It represents royalty, creativity, and leadership. It's associated with the heart and fire element."
  ),
  "Kanya (Virgo)" = list(
    date_range = c("September 16", "October 15"),
    stars = western_zodiac_data[["Virgo"]]$stars,
    lines = western_zodiac_data[["Virgo"]]$lines,
    info = "Kanya (Virgin) is ruled by Mercury in Vedic astrology. It represents analysis, service, and perfectionism. It's associated with the digestive system and earth element."
  ),
  "Tula (Libra)" = list(
    date_range = c("October 16", "November 14"),
    stars = western_zodiac_data[["Libra"]]$stars,
    lines = western_zodiac_data[["Libra"]]$lines,
    info = "Tula (Balance) is ruled by Venus in Vedic astrology. It represents balance, harmony, and relationships. It's associated with the lower back/kidneys and air element."
  ),
  "Vrishchika (Scorpio)" = list(
    date_range = c("November 15", "December 14"),
    stars = western_zodiac_data[["Scorpio"]]$stars,
    lines = western_zodiac_data[["Scorpio"]]$lines,
    info = "Vrishchika (Scorpion) is ruled by Mars in Vedic astrology. It represents transformation, intensity, and mysteries. It's associated with the reproductive organs and water element."
  ),
  "Dhanu (Sagittarius)" = list(
    date_range = c("December 15", "January 13"),
    stars = western_zodiac_data[["Sagittarius"]]$stars,
    lines = western_zodiac_data[["Sagittarius"]]$lines,
    info = "Dhanu (Archer) is ruled by Jupiter in Vedic astrology. It represents wisdom, philosophy, and expansion. It's associated with the thighs and fire element."
  ),
  "Makara (Capricorn)" = list(
    date_range = c("January 14", "February 12"),
    stars = western_zodiac_data[["Capricorn"]]$stars,
    lines = western_zodiac_data[["Capricorn"]]$lines,
    info = "Makara (Crocodile/Goat) is ruled by Saturn in Vedic astrology. It represents discipline, ambition, and structure. It's associated with the knees/joints and earth element."
  ),
  "Kumbha (Aquarius)" = list(
    date_range = c("February 13", "March 13"),
    stars = western_zodiac_data[["Aquarius"]]$stars,
    lines = western_zodiac_data[["Aquarius"]]$lines,
    info = "Kumbha (Water Bearer) is ruled by Saturn in Vedic astrology. It represents innovation, humanitarian efforts, and unconventional thinking. It's associated with the ankles and air element."
  ),
  "Meena (Pisces)" = list(
    date_range = c("March 14", "April 13"),
    stars = western_zodiac_data[["Pisces"]]$stars,
    lines = western_zodiac_data[["Pisces"]]$lines,
    info = "Meena (Fish) is ruled by Jupiter in Vedic astrology. It represents spirituality, dreams, and compassion. It's associated with the feet and water element."
  )
)

# Function to determine zodiac sign based on birthdate and system
get_zodiac_sign <- function(birth_month, birth_day, system = "western") {
  month_day <- paste(month.name[birth_month], birth_day, sep = " ")
  
  # Select the appropriate zodiac system data
  zodiac_data <- if(system == "western") western_zodiac_data else vedic_zodiac_data
  
  for (sign in names(zodiac_data)) {
    start_date <- as.Date(paste(zodiac_data[[sign]]$date_range[1], "2023"), format = "%B %d %Y")
    end_date <- as.Date(paste(zodiac_data[[sign]]$date_range[2], "2023"), format = "%B %d %Y")
    
    # Handle special case for Capricorn in Western system (spans December to January)
    if (system == "western" && sign == "Capricorn") {
      check_date <- as.Date(paste(month.name[birth_month], birth_day, "2023"), format = "%B %d %Y")
      if (birth_month == 12 || (birth_month == 1 && birth_day <= 19)) {
        return(sign)
      }
    } 
    # Handle special case for Makara in Vedic system (spans December to January)
    else if (system == "vedic" && sign == "Makara (Capricorn)") {
      check_date <- as.Date(paste(month.name[birth_month], birth_day, "2023"), format = "%B %d %Y")
      if ((birth_month == 12 && birth_day >= 15) || (birth_month == 1 && birth_day <= 14)) {
        return(sign)
      }
    } else {
      check_date <- as.Date(paste(month.name[birth_month], birth_day, "2023"), format = "%B %d %Y")
      if (!is.na(check_date) && !is.na(start_date) && !is.na(end_date)) {
        if (check_date >= start_date && check_date <= end_date) {
          return(sign)
        }
      }
    }
  }
  
  return("Unknown") # Default if no match found
}

# Define UI
ui <- fluidPage(
  theme = shinytheme("cyborg"),  # Dark theme for mystical feel
  tags$head(
    tags$style(HTML("
      .title {
        color: #9370DB;
        font-family: 'Arial', sans-serif;
        font-weight: bold;
        text-align: center;
        margin: 20px 0;
        text-shadow: 0px 0px 10px #9370DB;
      }
      .constellation-panel {
        border: 1px solid #9370DB;
        border-radius: 10px;
        padding: 15px;
        background-color: rgba(20, 20, 40, 0.7);
        box-shadow: 0px 0px 15px #9370DB;
      }
      .info-box {
        margin-top: 15px;
        padding: 10px;
        background-color: rgba(30, 30, 50, 0.7);
        border-radius: 5px;
        border-left: 3px solid #9370DB;
      }
      body {
        background-color: #121212;
        background-image: url('https://www.transparenttextures.com/patterns/star-dust.png');
      }
      .star-label {
        font-size: 12px;
        fill: #9370DB;
      }
      .system-toggle {
        background-color: rgba(30, 30, 50, 0.7);
        border-radius: 5px;
        padding: 10px;
        margin-bottom: 15px;
        text-align: center;
      }
      .system-toggle .shinyWidgets-radioGroupButtons label {
        color: #9370DB;
        background-color: rgba(20, 20, 40, 0.7);
        border-color: #9370DB;
      }
      .system-toggle .shinyWidgets-radioGroupButtons label.active {
        background-color: #9370DB;
        color: #121212;
        font-weight: bold;
      }
      .system-info {
        font-size: 0.85em;
        font-style: italic;
        margin-top: 5px;
        opacity: 0.8;
      }
    "))
  ),
  
  # Title with Hindi text
  div(class = "title", 
      h1("Personalized Constellation"),
      h3("थोड़ा रहस्यमय - A Little Mysterious")
  ),
  
  # Main layout
  sidebarLayout(
    sidebarPanel(
      class = "constellation-panel",
      
      # System toggle
      div(class = "system-toggle",
          h4("Choose Zodiac System:"),
          radioGroupButtons(
            inputId = "zodiac_system",
            label = NULL,
            choices = c("Western" = "western", "Vedic" = "vedic"),
            selected = "western",
            status = "primary",
            justified = TRUE,
            checkIcon = list(
              yes = icon("ok", lib = "glyphicon")
            )
          ),
          div(class = "system-info", 
              HTML("<p>Western (Tropical) vs Vedic (Sidereal) systems differ based on calculations accounting for the Earth's precession.</p>"))
      ),
      
      # Birthdate input
      dateInput("birthdate", 
                h4("Enter your birthdate:"),
                value = Sys.Date() - 365*25),
      
      # Display zodiac sign
      uiOutput("zodiac_title"),
      
      # Display date range
      uiOutput("date_range"),
      
      # Display constellation info
      uiOutput("constellation_info")
    ),
    
    mainPanel(
      class = "constellation-panel",
      plotOutput("constellation_plot", height = "500px")
    )
  )
)

# Define server logic
server <- function(input, output) {
  
  # Select the appropriate zodiac data based on system choice
  current_zodiac_data <- reactive({
    if(input$zodiac_system == "western") {
      western_zodiac_data
    } else {
      vedic_zodiac_data
    }
  })
  
  # Determine zodiac sign based on input date and selected system
  zodiac_sign <- reactive({
    req(input$birthdate)
    birth_month <- as.numeric(format(input$birthdate, "%m"))
    birth_day <- as.numeric(format(input$birthdate, "%d"))
    get_zodiac_sign(birth_month, birth_day, input$zodiac_system)
  })
  
  # Display zodiac title
  output$zodiac_title <- renderUI({
    sign <- zodiac_sign()
    if(sign != "Unknown") {
      h2(paste("Your Sign:", sign), style = "color: #9370DB; text-align: center;")
    } else {
      h2("Please enter a valid date", style = "color: red; text-align: center;")
    }
  })
  
  # Display date range
  output$date_range <- renderUI({
    sign <- zodiac_sign()
    if(sign != "Unknown") {
      date_range <- current_zodiac_data()[[sign]]$date_range
      h4(paste("Date Range:", date_range[1], "-", date_range[2]), 
         style = "color: #9370DB; text-align: center;")
    }
  })
  
  # Display constellation info
  output$constellation_info <- renderUI({
    sign <- zodiac_sign()
    if(sign != "Unknown") {
      info <- current_zodiac_data()[[sign]]$info
      div(class = "info-box",
          h4("About this constellation:"),
          if(input$zodiac_system == "vedic") {
            HTML(paste("<p><strong>Vedic Name:</strong> ", sign, "</p>", info))
          } else {
            p(info)
          }
      )
    }
  })
  
  # Render constellation plot
  output$constellation_plot <- renderPlot({
    sign <- zodiac_sign()
    if(sign != "Unknown") {
      # Get constellation data
      stars <- current_zodiac_data()[[sign]]$stars
      lines <- current_zodiac_data()[[sign]]$lines
      
      # Create plot
      p <- ggplot() +
        # Add lines connecting stars
        geom_path(data = lines, aes(x = x, y = y, group = group), 
                  color = "#9370DB", alpha = 0.6, size = 1) +
        # Add stars
        geom_point(data = stars, aes(x = x, y = y), 
                   color = "white", size = 8, alpha = 0.8) +
        # Add smaller bright center to stars
        geom_point(data = stars, aes(x = x, y = y), 
                   color = "#E6E6FA", size = 4) +
        # Add star labels
        geom_text(data = stars, aes(x = x, y = y + 0.2, label = name), 
                  color = "#9370DB", size = 4, fontface = "bold") +
        # Add background stars (random dots)
        geom_point(data = data.frame(
          x = runif(200, -1, 6),
          y = runif(200, -1, 5)
        ), aes(x = x, y = y), color = "white", size = 0.5, alpha = 0.5) +
        # Theme and styling
        theme_void() +
        theme(
          plot.background = element_rect(fill = "#121212", color = NA),
          panel.background = element_rect(fill = "#121212", color = NA),
          plot.title = element_text(color = "#9370DB", size = 20, face = "bold", hjust = 0.5)
        ) +
        coord_cartesian(xlim = c(0, 5.5), ylim = c(0, 4.5)) +
        ggtitle(paste(sign, "Constellation"))
      
      return(p)
    } else {
      # Default empty plot
      ggplot() + 
        theme_void() + 
        theme(
          plot.background = element_rect(fill = "#121212", color = NA)
        ) +
        ggtitle("Please enter a valid birthdate")
    }
  })
}

# Run the application 
shinyApp(ui = ui, server = server)
