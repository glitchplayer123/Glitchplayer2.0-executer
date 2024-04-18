-- Create a ScreenGui to hold the GUI
local gui = Instance.new("ScreenGui")
gui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")

-- Create a Frame to hold the elements
local frame = Instance.new("Frame")
frame.Size = UDim2.new(0, 400, 0, 300)  -- Adjust the size as needed
frame.Position = UDim2.new(0.5, -200, 0.5, -150)  -- Center the frame initially
frame.BackgroundColor3 = Color3.new(0, 0, 0)  -- Set background color
frame.BackgroundTransparency = 0.5  -- Adjust transparency as needed
frame.Active = true  -- Make the frame interactable
frame.Draggable = true  -- Make the frame draggable
frame.Parent = gui

-- Create a label at the top
local topLabel = Instance.new("TextLabel")
topLabel.Text = "Made by glitchplayer 2.0"
topLabel.Size = UDim2.new(1, 0, 0, 30)  -- Set height to 30 pixels
topLabel.TextColor3 = Color3.new(1, 1, 1)  -- Set text color to white
topLabel.BackgroundTransparency = 1  -- Make background transparent
topLabel.Parent = frame

-- Create a TextBox in the middle for Lua script
local scriptTextBox = Instance.new("TextBox")
scriptTextBox.Text = "-- Write your Lua script here"
scriptTextBox.Size = UDim2.new(1, -20, 1, -100)  -- Adjust size leaving space for buttons
scriptTextBox.Position = UDim2.new(0, 10, 0, 40)  -- Position leaving space at top
scriptTextBox.MultiLine = true  -- Enable multi-line
scriptTextBox.TextWrapped = true  -- Enable text wrapping
scriptTextBox.Parent = frame

-- Create a TextButton at the bottom-left to delete the executer
local deleteButton = Instance.new("TextButton")
deleteButton.Text = "Delete Executer"
deleteButton.Size = UDim2.new(0, 150, 0, 30)  -- Adjust size to fit text
deleteButton.Position = UDim2.new(0, 10, 1, -50)  -- Position at the bottom-left
deleteButton.Parent = frame

-- Create a TextButton at the bottom-right to execute the script
local executeButton = Instance.new("TextButton")
executeButton.Text = "Execute"
executeButton.Size = UDim2.new(0, 150, 0, 30)  -- Adjust size to fit text
executeButton.Position = UDim2.new(1, -160, 1, -50)  -- Position at the bottom-right
executeButton.Parent = frame

-- Create a TextButton at the bottom in the middle to clear the script
local clearButton = Instance.new("TextButton")
clearButton.Text = "Clear Script"
clearButton.Size = UDim2.new(0, 150, 0, 30)  -- Adjust size to fit text
clearButton.Position = UDim2.new(0.5, -75, 1, -50)  -- Position at the bottom in the middle
clearButton.Parent = frame

-- Create a search logo
local searchLogo = Instance.new("ImageButton")
searchLogo.Size = UDim2.new(0, 30, 0, 30)  -- Set size to square
searchLogo.Position = UDim2.new(1, -40, 0, 10)  -- Position at the top-right
searchLogo.Image = "rbxassetid://10468797"  -- Set the search logo asset ID
searchLogo.BackgroundTransparency = 1  -- Make the background transparent
searchLogo.Parent = frame

-- Function to handle button click
local function onClick()
    local script = scriptTextBox.Text
    local success, errorMsg = pcall(loadstring(script))
    if not success then
        warn("Error executing script:", errorMsg)
    else
        print("Script executed successfully!")
    end
end

-- Connect button click event to the onClick function
executeButton.MouseButton1Click:Connect(onClick)

-- Function to handle delete button click
local function onDeleteClick()
    gui:Destroy()  -- Delete the GUI when clicked
end

-- Connect delete button click event to the onDeleteClick function
deleteButton.MouseButton1Click:Connect(onDeleteClick)

-- Function to handle clear button click
local function onClearClick()
    scriptTextBox.Text = "-- Write your Lua script here"  -- Clear the Lua script text
end

-- Connect clear button click event to the onClearClick function
clearButton.MouseButton1Click:Connect(onClearClick)

-- Function to handle search logo click
local function onSearchLogoClick()
    -- Add code here to execute a search script (powered by scriptblox.com)
    print("Search logo clicked!")
    -- Example: You can open a web browser to a search page
    -- game:GetService("GuiService"):OpenBrowserWindow("https://scriptblox.com/search?q=")
end

-- Connect search logo click event to the onSearchLogoClick function
searchLogo.MouseButton1Click:Connect(onSearchLogoClick)
