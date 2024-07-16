# frames_from_video
#this algorithm will help you to extract frames from mp4 video
# Input video file path
video_file = 'video.mp4'

# Output directory for saving screenshots
output_dir = 'new1'

# Create the output directory if it doesn't exist
if not os.path.exists(output_dir):
    os.makedirs(output_dir)

# Open the video file
cap = cv2.VideoCapture(video_file)

# Initialize a frame counter
frame_count = 0

while True:
    # Read a frame from the video
    ret, frame = cap.read()

    # Break the loop if we have reached the end of the video
    if not ret:
        break

    # Save the frame as an image
    frame_filename = os.path.join(output_dir, f'frame_{frame_count:04d}.png')
    cv2.imwrite(frame_filename, frame)

    # Increment the frame counter
    frame_count += 1

# Release the video capture object and close any open windows
cap.release()
cv2.destroyAllWindows()
print(f"Frames captured and saved in '{output_dir}'")

